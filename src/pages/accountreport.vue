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
  <VRow class="match-height"><v-breadcrumbs :items="['Home', 'AAPL', 'Reports']"></v-breadcrumbs></VRow>
  <VRow class="match-height">
    <VCol
      cols="12"
      md="12"
    >
      <h3 class="pb-3">Report Q3 2024</h3>
      <div class="d-flex">
        <VCol
          cols="12"
          md="6"
        >
          <h4>
            The pdf summarized: Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
            incididunt ut labore et dolore magna aliqua. Ut enim ad
          </h4>
        </VCol>
        <VCol
          cols="12"
          md="3"
        >
          <div class="d-flex justify-end jutify-column">
            <h4>
              <VIcon icon="ri-mail-line" />
              Email the summary
            </h4>
          </div>
        </VCol>
      </div>
    </VCol>
    <VCol
      cols="12"
      md="12"
    >
      <h3 class="pb-3">Report Analysis</h3>
      <div class="d-flex">
        <VCol
          cols="12"
          md="8"
        >
          <h4>Ask followup question on this report.</h4>
        </VCol>
        <VCol
          cols="12"
          md="3"
        >
          <div class="d-flex justify-end jutify-column">
            <v-btn>Use Assistant to Analyze</v-btn>
          </div>
        </VCol>
      </div>
    </VCol>
    <VCol
      cols="12"
      md="12"
    >
      <v-sheet
        class="pa-12"
        color="grey-lighten-3"
      >
        <div></div>
        <v-sheet
          rounded
          class="mx-auto"
          height="700"
          width="100"
          ><div>Pdf content</div></v-sheet
        >
        <div></div>
      </v-sheet>
    </VCol>
  </VRow>
</template>
