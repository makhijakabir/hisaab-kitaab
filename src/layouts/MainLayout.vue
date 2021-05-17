<template>
  <q-layout view="lHh LpR lFf">
    <q-header
      reveal
      :class="$q.dark.isActive ? 'header_dark' : 'header_normal'"
    >
      <q-toolbar>
        <q-btn
          @click="left = !left"
          flat
          round
          dense
          icon="menu"
          class="q-mr-sm"
        />
        <!--          <q-avatar>-->
        <!--            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">-->
        <!--          </q-avatar>-->

        <q-toolbar-title>HISAAB KITAAB</q-toolbar-title>
        <q-btn
          class="q-mr-xs"
          flat
          round
          @click="$q.dark.toggle()"
          :icon="$q.dark.isActive ? 'nights_stay' : 'wb_sunny'"
        />

        <q-btn flat round dense icon="search" class="q-mr-xs" />
        <q-btn
          flat
          round
          dense
          icon="fas fa-sign-out-alt"
          @click="logoutNotify"
          to="/"
        />
      </q-toolbar>
    </q-header>
    <q-drawer
      class="left-navigation text-white"
      show-if-above
      v-model="left"
      style="background-image: url(https://images.unsplash.com/photo-1521737711867-e3b97375f902?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=334&q=80) !important;"
      side="left"
      elevated
    >
      <div
        class="full-height"
        :class="$q.dark.isActive ? 'drawer_dark' : 'drawer_normal'"
      >
        <div style="height: calc(100% - 117px);padding:10px;">
          <q-toolbar>
            <q-avatar>
              <img src="https://avatars.githubusercontent.com/u/63370746?s=400&u=096f0c5cff281492d3cf8352c1200cfc014a9faf&v=4" />
            </q-avatar>

            <q-toolbar-title>Kabir Makhija</q-toolbar-title>
          </q-toolbar>
          <hr />
          <q-scroll-area style="height:100%;">
            <q-list padding>
              <q-item
                active-class="tab-active"
                to="/dashboard"
                exact
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="dashboard" />
                </q-item-section>

                <q-item-section>
                  Dashboard
                </q-item-section>
              </q-item>

              <!-- In order to maintain the versatility of the applicaition, different versisons are created -->

              <!-- <q-item
                active-class="tab-active"
                to="/dashboard_v2"
                exact
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="dashboard" />
                </q-item-section>

                <q-item-section>
                  Dashboard v2
                </q-item-section>
              </q-item> -->

              <!-- <q-item
                active-class="tab-active"
                to="/dashboard_v3"
                exact
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="dashboard" />
                </q-item-section>

                <q-item-section>
                  Dashboard v3
                </q-item-section>
              </q-item> -->

              <q-item
                active-class="tab-active"
                to="/customer_management"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="star" />
                </q-item-section>

                <q-item-section>
                  Our Customes
                </q-item-section>
              </q-item>

              <q-item
                active-class="tab-active"
                to="/change_request"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="send" />
                </q-item-section>

                <q-item-section>
                  Ammendment Requests
                </q-item-section>
              </q-item>

              <q-item
                active-class="tab-active"
                to="/sales_invoices"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="attach_money" />
                </q-item-section>

                <q-item-section>
                  Sales Invoices
                </q-item-section>
              </q-item>

              <!-- <q-item
                active-class="tab-active"
                to="/quotes"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="money" />
                </q-item-section>

                <q-item-section>
                  Quotes
                </q-item-section>
              </q-item> -->

              <q-item
                active-class="tab-active"
                to="/transactions"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="assignment" />
                </q-item-section>

                <q-item-section>
                  Transactions
                </q-item-section>
              </q-item>

              <q-item
                active-class="tab-active"
                to="/employee_salary_list"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="list" />
                </q-item-section>

                <q-item-section>
                  Employee Salary 
                </q-item-section>
              </q-item>

              <q-item
                active-class="tab-active"
                to="/calendar"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="calendar_today" />
                </q-item-section>

                <q-item-section>
                  Engagements
                </q-item-section>
              </q-item>

              <q-item
                active-class="tab-active"
                to="/department"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="business" />
                </q-item-section>

                <q-item-section>
                  My Department
                </q-item-section>
              </q-item>

              <q-item
                active-class="tab-active"
                to="/my_profile"
                class="q-ma-sm navigation-item"
                clickable
                v-ripple
              >
                <q-item-section avatar>
                  <q-icon name="drafts" />
                </q-item-section>

                <q-item-section>
                  My Profile
                </q-item-section>
              </q-item>
            </q-list>
          </q-scroll-area>
        </div>
      </div>
    </q-drawer>

    <q-page-container>
      <q-page class="row no-wrap">
        <div class="col">
          <div class="full-height">
            <q-scroll-area class="col q-pr-sm full-height" visible>
              <router-view />
            </q-scroll-area>
          </div>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data() {
    return {
      left: false
    };
  },
  methods: {
    logoutNotify() {
      this.$q.notify({
        message: "Logged out"
      });
    }
  }
};
</script>

<style>
.q-drawer {
  /* background-image: url(https://demos.creative-tim.com/vue-material-dashboard/img/sidebar-2.32103624.jpg) !important; */
  background-image: url("https://images.unsplash.com/photo-1504432842672-1a79f78e4084?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MTR8fG1vdGl2YXRpb258ZW58MHx8MHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60") !important;
  background-size: cover !important;
}

.drawer_normal {
  background-color: rgba(1, 1, 1, 0.75);
}

.drawer_dark {
  background-color: #000000;
}

.navigation-item {
  border-radius: 5px;
}

.tab-active {
  background-color: black;
}

body {
  background: #ffffff !important;
}

.header_normal {
  background: linear-gradient(
    145deg,
    #000000 15%,
    #3d3d3d 70%
  );
}

.header_dark {
  background: linear-gradient(145deg, #000000 15%, #3d3d3d 70%);
}
</style>
