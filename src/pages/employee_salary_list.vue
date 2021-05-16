<template>
  <q-page class="q-pa-sm">
    <q-card>
      <q-table
        title="Employee Salary Breakup"
        :data="data"
        :hide-header="mode === 'grid'"
        :columns="columns"
        row-key="name"
        :grid="mode=='grid'"
        :filter="filter"
        :pagination.sync="pagination"
      >
        <template v-slot:top-right="props">
          <q-input outlined dense debounce="300" v-model="filter" placeholder="Search">
            <template v-slot:append>
              <q-icon name="search"/>
            </template>
          </q-input>

          <q-btn
            flat
            round
            dense
            :icon="props.inFullscreen ? 'fullscreen_exit' : 'fullscreen'"
            @click="props.toggleFullscreen"
            v-if="mode === 'list'"
          >
            <q-tooltip
              :disable="$q.platform.is.mobile"
              v-close-popup
            >{{props.inFullscreen ? 'Exit Fullscreen' : 'Toggle Fullscreen'}}
            </q-tooltip>
          </q-btn>

          <q-btn
            flat
            round
            dense
            :icon="mode === 'grid' ? 'list' : 'grid_on'"
            @click="mode = mode === 'grid' ? 'list' : 'grid'; separator = mode === 'grid' ? 'none' : 'horizontal'"
            v-if="!props.inFullscreen"
          >
            <q-tooltip
              :disable="$q.platform.is.mobile"
              v-close-popup
            >{{mode==='grid' ? 'List' : 'Grid'}}
            </q-tooltip>
          </q-btn>

          <q-btn
            color="primary"
            icon-right="archive"
            label="Export to csv"
            no-caps
            @click="exportTable"
          />
        </template>
        <template v-slot:body-cell-detail="props">
          <q-td :props="props">
            <q-btn @click="employee_dialog=true" dense round color="secondary" icon="pageview"/>
          </q-td>
        </template>
        <template v-slot:body-cell-action="props">
          <q-td :props="props">
            <div class="q-gutter-sm">
              <q-btn dense color="primary" icon="edit"/>
              <q-btn dense color="red" icon="delete"/>
            </div>
          </q-td>
        </template>
      </q-table>
    </q-card>

    <q-dialog v-model="employee_dialog">
      <q-card class="my-card" flat bordered>
        <q-card-section>
          <div class="text-h6">
            Employee Details
            <q-btn round flat dense icon="close" class="float-right" color="grey-8" v-close-popup></q-btn>
          </div>
        </q-card-section>
        <q-card-section horizontal>
          <q-card-section class="q-pt-xs">
            <div class="text-overline">IND Region</div>
            <div class="text-h5 q-mt-sm q-mb-xs"></div>
            <div class="text-caption text-grey">
              Sales and Marketing Executive | Graduate and past committee | Keynote speaker on Selling and Recruiting
              Topics
            </div>
          </q-card-section>

          <q-card-section class="col-5 flex flex-center">
            <q-img
              class="rounded-borders"
              src="https://images.unsplash.com/photo-1617074075387-be5051758663?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Zm9ybWFsJTIwd29tYW58ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60"
            />
          </q-card-section>
        </q-card-section> 

        <q-separator/>

        <q-card-section>
          Assessing clients needs and present suitable promoted products. Liaising with and persuading targeted doctors
          to prescribe our products utilizing effective sales skills.
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script>
    import {exportFile} from "quasar";

    function wrapCsvValue(val, formatFn) {
        let formatted = formatFn !== void 0 ? formatFn(val) : val;

        formatted =
            formatted === void 0 || formatted === null ? "" : String(formatted);

        formatted = formatted.split('"').join('""');

        return `"${formatted}"`;
    }

    export default {
        data() {
            return {
                filter: "",
                mode: "list",
                invoice: {},
                employee_dialog: false,
                columns: [
                    {
                        name: "serial_no",
                        align: "left",
                        label: "Serial No.",
                        field: "serial_no",
                        sortable: true
                    },
                    {
                        name: "emp_id",
                        required: true,
                        label: "Employee Id",
                        align: "left",
                        field: "emp_id",
                        sortable: true
                    },
                    {
                        name: "name",
                        align: "left",
                        label: "Employee Name",
                        field: "name",
                        sortable: true
                    },
                    {
                        name: "salary_type",
                        align: "left",
                        label: "Salary Type",
                        field: "salary_type",
                        sortable: true
                    },
                    {
                        name: "basic_salary",
                        align: "left",
                        label: "Basic salary",
                        field: "basic_salary",
                        sortable: true
                    },
                    {
                        name: "overtime",
                        align: "left",
                        label: "Overtime",
                        field: "overtime",
                        sortable: true
                    },
                    {
                        name: "detail",
                        align: "left",
                        label: "Detail",
                        field: "detail",
                        sortable: true
                    },
                    {
                        name: "action",
                        align: "left",
                        label: "Action",
                        field: "action",
                        sortable: true
                    }
                ],
                data: [
                    {
                        serial_no: "01",
                        emp_id: "Emp 233",
                        name: "Vedika Narayan",
                        basic_salary: "₹ 40,000/-",
                        salary_type: "Basic",
                        overtime: "₹ 1,000/-",
                    },
                    {
                        serial_no: "02",
                        emp_id: "Emp 104",
                        name: "Aaradhya Rawat",
                        basic_salary: "₹ 40,000/-",
                        salary_type: "Basic",
                        overtime: "₹ 1,000/-",
                    },
                    {
                        serial_no: "03",
                        emp_id: "Emp 345",
                        name: "Fatima Mirza",
                        basic_salary: "₹ 37,000/-",
                        salary_type: "Basic",
                        overtime: "₹ 1,000",
                    },
                    {
                        serial_no: "04",
                        emp_id: "Emp 217",
                        name: "Anna Marie",
                        basic_salary: "₹ 37,000/-",
                        salary_type: "Basic",
                        overtime: "₹ 1,000",
                    },
                ],
                pagination: {
                    rowsPerPage: 10
                }
            };
        },
        methods: {
            exportTable() {
                // naive encoding to csv format
                const content = [this.columns.map(col => wrapCsvValue(col.label))]
                    .concat(
                        this.data.map(row =>
                            this.columns
                                .map(col =>
                                    wrapCsvValue(
                                        typeof col.field === "function"
                                            ? col.field(row)
                                            : row[col.field === void 0 ? col.name : col.field],
                                        col.format
                                    )
                                )
                                .join(",")
                        )
                    )
                    .join("\r\n");

                const status = exportFile("employee_salary_list.csv", content, "text/csv");

                if (status !== true) {
                    this.$q.notify({
                        message: "Browser denied file download...",
                        color: "negative",
                        icon: "warning"
                    });
                }
            }
        }
    };
</script>
<style>
  .q-chip__content {
    display: block;
    text-align: center;
  }
</style>
