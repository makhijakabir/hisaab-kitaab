<template>
  <q-page>
    <h5 class="q-my-xs q-pt-sm q-ml-md text-black">The Departments I Manage</h5>
    <div class="row q-col-gutter-sm q-ma-xs q-mr-sm">
      
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <q-card flat bordered class="">
          <q-card-section class="row">
            <div class="text-h6 col-12">Team Alpha
            </div>
          </q-card-section>

          <q-separator inset></q-separator>

          <q-card-section>
            <q-table
              :data="team_data"
              :columns="columns"
              row-key="name"
              :pagination.sync="pagination"
            >
              <template v-slot:body-cell-action="props">
                <q-td :props="props">
                  <div class="q-gutter-sm">
                    <q-btn dense color="primary" icon="edit"/>
                    <q-btn dense color="red" icon="delete"/>
                  </div>
                </q-td>
              </template>
            </q-table>
          </q-card-section>
        </q-card>
      </div>

      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <q-card flat bordered class="">
          <q-card-section class="row">
            <div class="text-h6 col-12">Team Beta
            </div>
          </q-card-section>

          <q-separator inset></q-separator>

          <q-card-section>
            <q-table
              :data="team_data"
              :columns="columns"
              row-key="name"
              :pagination.sync="pagination"
            >
              <template v-slot:body-cell-action="props">
                <q-td :props="props">
                  <div class="q-gutter-sm">
                    <q-btn dense color="primary" icon="edit"/>
                    <q-btn dense color="red" icon="delete"/>
                  </div>
                </q-td>
              </template>
            </q-table>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <q-card flat bordered class="">
          <q-card-section class="row">
            <div class="text-h6 col-12">Team Gamma
            </div>
          </q-card-section>

          <q-separator inset></q-separator>

          <q-card-section>
            <q-table
              :data="team_data"
              :columns="columns"
              row-key="name"
              :pagination.sync="pagination"
            >
              <template v-slot:body-cell-action="props">
                <q-td :props="props">
                  <div class="q-gutter-sm">
                    <q-btn dense color="primary" icon="edit"/>
                    <q-btn dense color="red" icon="delete"/>
                  </div>
                </q-td>
              </template>
            </q-table>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <q-card flat bordered class="">
          <q-card-section class="row">
            <div class="text-h6 col-12">Team Delta
            </div>
          </q-card-section>

          <q-separator inset></q-separator>

          <q-card-section>
            <q-table
              :data="team_data"
              :columns="columns"
              row-key="name"
              :pagination.sync="pagination"
            >
              <template v-slot:body-cell-action="props">
                <q-td :props="props">
                  <div class="q-gutter-sm">
                    <q-btn dense color="primary" icon="edit"/>
                    <q-btn dense color="red" icon="delete"/>
                  </div>
                </q-td>
              </template>
            </q-table>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
    export default {
        data() {
            return {
                columns: [
                    {
                        name: "serial_no",
                        align: "left",
                        label: "Serial No.",
                        field: "serial_no",
                        sortable: true
                    },
                    {
                        name: "designation",
                        align: "left",
                        label: "Designation",
                        field: "designation",
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
                team_data: [
                    {
                        serial_no: "01",
                        designation: "Chief Manager",
                    },
                    {
                        serial_no: "02",
                        designation: "Assistant Manager A",
                    },
                    {
                        serial_no: "03",
                        designation: "Assistant Manager B",
                    },
                    {
                        serial_no: "04",
                        designation: "Assistant Manager c",
                    },
                    {
                        serial_no: "05",
                        designation: "Assistant Manager D",
                    }
                ],
                pagination: {
                    rowsPerPage: 5
                }
            }
        }
    }
</script>
