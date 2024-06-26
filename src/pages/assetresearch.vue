<script setup>
import MartketSentiment from '@/views/pages/assetresearch/marketsentiment.vue'
import CardCarousel from '@/views/pages/assetresearch/cardcarousel.vue'
import SummaryTable from '@/views/pages/assetresearch/summarytable.vue'
import { VBtn, VCard, VRow } from 'vuetify/lib/components/index.mjs'

const totalProfit = {
  title: 'Total Profit',
  color: 'secondary',
  icon: 'ri-pie-chart-2-line',
  stats: '$25.6k',
  change: 42,
  subtitle: 'Weekly Project',
}

const newProject = {
  title: 'New Project',
  color: 'primary',
  icon: 'ri-file-word-2-line',
  stats: '862',
  change: -18,
  subtitle: 'Yearly Project',
}

const navigationTab = ref('Portfolio')

const tabItems = ['Portfolio', 'Trading desk']
</script>

<template>
  <VRow class="match-height"><v-breadcrumbs :items="['Home', 'AAPL']"></v-breadcrumbs></VRow>
  <VRow class="match-height">
    <VCol
      cols="12"
      md="12"
    >
      <h1 class="text-center pb-3">AAPL Inc. (AAPL)</h1>
      <h3 class="text-center pb-3">Exchange (NASDAQ)</h3>
      <v-divider></v-divider>
      <div class="d-flex justify-center">
        <VCol
          cols="6"
          md="4"
        >
          <h2>Share Price</h2>
        </VCol>
        <VCol
          cols="6"
          md="2"
        >
          <h2>$100</h2>
        </VCol>
      </div>

      <div class="d-flex align-center justify-center">
        <VCol
          cols="6"
          md="4"
        >
          <h2>Average Cost Basis</h2>
        </VCol>
        <VCol
          cols="6"
          md="2"
        >
          <h2>$32.60</h2>
        </VCol>
      </div>
      <div class="d-flex align-center justify-center">
        <VCol
          cols="6"
          md="4"
        >
          <h2>Current Holdings</h2>
        </VCol>
        <VCol
          cols="6"
          md="2"
        >
          <h2>$1,732</h2>
        </VCol>
      </div>
      <div class="d-flex justify-center">
        <VCol
          cols="6"
          md="4"
        >
          <VBtn
            style="width: 200px"
            color="success"
            >Buy</VBtn
          >
        </VCol>
        <VCol
          cols="6"
          md="4"
        >
          <v-btn
            style="width: 200px"
            color="error"
            >Sell</v-btn
          >
        </VCol>
      </div>
      <div class="d-flex">
        <VCol
          cols="6"
          md="6"
          ><v-card
            outlined
            class="mx-auto"
          >
            <v-row
              no-gutters
              class="pa-3"
              ><v-col
                cols="7"
                class="my-auto pl-6"
              >
                <h4 class="text-h2 text-primary">Daily P & L</h4>
              </v-col>
              <v-col cols="3"
                ><v-row
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
                </v-row></v-col
              ></v-row
            >
          </v-card></VCol
        >
        <VCol
          cols="6"
          md="6"
          ><v-card
            outlined
            class="mx-auto"
          >
            <v-row
              no-gutters
              class="pa-3"
              ><v-col
                cols="7"
                class="my-auto pl-6"
              >
                <h4 class="text-h2 text-primary">Total P & L</h4>
              </v-col>
              <v-col cols="3"
                ><v-row
                  no-gutters
                  class="pb-5"
                >
                  <div>
                    <div class="text-h5 green--text text-success">
                      <VIcon
                        size="24"
                        icon="ri-arrow-up-s-line"
                        color="success"
                      />$523
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
                      />47.3%
                      <v-icon color="success"> mdi-arrow-top-right</v-icon>
                    </div>
                  </div>
                </v-row></v-col
              ></v-row
            >
          </v-card></VCol
        >
      </div>
    </VCol>

    <VCol
      cols="12"
      md="12"
    >
      <div class="d-flex pb-4">
        <VCol
          cols="6"
          md="6"
          ><v-card
            outlined
            class="mx-auto"
          >
          </v-card
        ></VCol>
        <VCol
          cols="6"
          md="6"
        >
          <v-row
            no-gutters
            class="pa-3"
          >
            <MartketSentiment></MartketSentiment
          ></v-row>
        </VCol>
      </div>
      <v-divider></v-divider>
      <div class="d-flex pt-4 justify-space-between">
        <VCol
          cols="6"
          md="6"
          class="d-flex flex-column justify-space-between"
          ><div class="d-flex justify-center pa-2"><h1 class="text-center pb-10">Assistant Recommendation</h1></div>
          <div>
            <div class="text-h3 d-flex justify-center pa-1 green--text text-success">Buy</div>
            <div class="text-h3 d-flex justify-center green--text text-success">76% confidence</div>
          </div>

          <div class="text-right"><v-btn>See Why</v-btn></div>
        </VCol>
        <VCol
          cols="6"
          md="6"
        >
          <v-row
            no-gutters
            class="pa-3"
          >
            <MartketSentiment></MartketSentiment
          ></v-row>
        </VCol>
      </div>
      <div class="d-flex pt-4 justify-space-between">
        <CardCarousel />
      </div>
      <div class="d-flex pt-4 justify-space-between">
        <div class="text-h4 pt-5">Existing reports and documents</div>
      </div>
      <div class="d-flex pt-4 justify-space-between">
          <v-row>
            <v-col cols="12" md="8">
              <h4>Missing documents? Upload a new one</h4>
              <h4>(Earning reports, 10-K reports, News articles, etc)</h4>
            </v-col>
            <v-col class="d-flex justify-end" cols="12" md="3">
              <v-btn>upload a doc</v-btn><v-icon class="grey--text text--darken-2" size="64">mdi-file</v-icon>
            </v-col>
          </v-row>
      </div>
      <div class="d-flex pt-4 justify-space-between">
        <SummaryTable/>
      </div>
    </VCol>
  </VRow>
</template>
