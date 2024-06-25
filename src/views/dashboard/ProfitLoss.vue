<script setup>
import trophy from '@images/misc/trophy.png'
</script>

<template>
  <VCard class="position-relative">
    <VCardText>
      <div class="mb-2">
        <h5 class="text-h5">Profits / Losses</h5>
      </div>
      <v-row
        no-gutters
        class="pb-3"
      >
        <v-col
          cols="7"
          class="my-auto pl-6"
        >
          <h4 class="text-h2 text-primary">Daily P & L</h4>
        </v-col>
        <v-col cols="3">
          <v-row
            no-gutters
            class="pb-5"
          >
            <div>
              <div class="text-h5 green--text text-success">
                <VIcon
                  size="24"
                  icon="ri-arrow-up-s-line"
                  color="success"
                />$123
              </div>
            </div>
          </v-row>
          <v-row
            no-gutters
            class="pb-5"
          >
            <div>
              <div class="text-h5 green--text text-success">
                <VIcon
                  size="24"
                  icon="ri-arrow-up-s-line"
                  color="success"
                />.03%
                <v-icon color="success"> mdi-arrow-top-right</v-icon>
              </div>
            </div>
          </v-row>
        </v-col>
      </v-row>
      <v-divider></v-divider>
      <v-row
        no-gutters
        class="pb-3 mt-3"
      >
        <v-col
          cols="7"
          class="my-auto pl-6"
        >
          <h4 class="text-h2 text-primary">Total P & L</h4>
        </v-col>
        <v-col cols="3">
          <v-row
            no-gutters
            class="pb-5"
          >
            <div>
              <div class="text-h5 green--text text-success">
                <VIcon
                  size="24"
                  icon="ri-arrow-up-s-line"
                  color="success"
                />$123
                <v-icon color="success"> mdi-arrow-top-right</v-icon>
              </div>
            </div>
          </v-row>
          <v-row
            no-gutters
            class="pb-5"
          >
            <div>
              <div class="text-h5 green--text text-success">
                <VIcon
                  size="24"
                  icon="ri-arrow-up-s-line"
                  color="success"
                />.03%
                <v-icon color="success"> mdi-arrow-top-right</v-icon>
              </div>
            </div>
          </v-row>
        </v-col>
      </v-row>
    </VCardText>
  </VCard>
</template>

<style lang="scss">
.v-card .trophy {
  position: absolute;
  inline-size: 5.188rem;
  inset-block-end: 1.25rem;
  inset-inline-end: 1.25rem;
}
</style>
