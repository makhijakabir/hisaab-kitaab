<template>
  <q-page>
    <div class="row q-col-gutter-sm q-ma-xs">
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <q-card class="my-card" flat bordered>
          <q-card-section horizontal>
            <q-card-section class="q-pt-xs">
              <div class="text-overline">IND Region</div>
              <div class="text-h5 q-mt-sm q-mb-xs">Kabir Makhija</div>
              <div class="text-caption text-grey">
                Sales & Operations Manager | TEDx Speaker | Promt Analyst on Innovation and Selling Methods
              </div>
            </q-card-section>

            <q-card-section class="col-5 flex flex-center">
              <q-img
                class="rounded-borders"
                src="https://avatars.githubusercontent.com/u/63370746?s=400&u=096f0c5cff281492d3cf8352c1200cfc014a9faf&v=4" />
            </q-card-section>
          </q-card-section>

          <q-separator/>

          <q-card-section>
            Addressing needs of our customers and helping the operations and innovations team out with new and effective methodologies.
          </q-card-section>
        </q-card>
      </div>
      <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
        <q-card>
          <q-card-section>
            <q-form
              class="q-gutter-md"
            >
              <q-input
                filled
                v-model="user.first_name"
                label="First Name"
              />

              <q-input
                filled
                v-model="user.last_name"
                label="Last Name"

              />

              <q-input
                filled
                v-model="user.age"
                label="Age"

              />

              <q-input
                filled
                v-model="user.email"
                label="Email"

              />

              <q-input
                filled
                v-model="user.phone"
                label="Phone"

              />

              <div>
                <q-btn label="Update" type="submit" color="primary"/>
              </div>
            </q-form>
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
                user: {
                    first_name: 'Kabir',
                    last_name: 'Makhija',
                    age: 20,
                    email: 'kabirmakhija05@gmail.com',
                    phone: '+91 73886 87536'
                },
            }
        },
    }
</script>

<style scoped>

</style>
