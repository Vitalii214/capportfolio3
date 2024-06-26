<script setup>
import ProfitLoss from '@/views/dashboard/ProfitLoss.vue'
import AnalyticsBarCharts from '@/views/dashboard/AnalyticsBarCharts.vue'
import AnalyticsDepositWithdraw from '@/views/dashboard/AnalyticsDepositWithdraw.vue'
import AnalyticsSalesByCountries from '@/views/dashboard/AnalyticsSalesByCountries.vue'
import AnalyticsTotalEarning from '@/views/dashboard/AnalyticsTotalEarning.vue'
import AnalyticsTotalProfitLineCharts from '@/views/dashboard/AnalyticsTotalProfitLineCharts.vue'
import AssetAllocation from '@/views/dashboard/AssetAllocation.vue'
import AnalyticsUserTable from '@/views/dashboard/AnalyticsUserTable.vue'
import AnalyticsWeeklyOverview from '@/views/dashboard/AnalyticsWeeklyOverview.vue'
import CardStatisticsVertical from '@core/components/cards/CardStatisticsVertical.vue'
import IndustryPieCharts from '@/views/dashboard/IndustryPieCharts.vue'
import LiquidCash from '@/views/dashboard/LiquidCash.vue'
import PortfolioLineCharts from '@/views/dashboard/PortfolioLineCharts.vue'
import PortfolioDetailsTable from '@/views/dashboard/PortfolioDetailsTable.vue'
import LiquidCashTable from '@/views/dashboard/LiquidCashTable.vue'
import { VRow } from 'vuetify/lib/components/index.mjs'

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
  <VRow class="match-height">
    <VCol
      cols="12"
      md="12"
    >
      <h1 class="text-center pb-3">Portfolio Summary</h1>
      <v-divider></v-divider>
      <div class="d-flex align-center justify-center">
        <h2 class="text-center pt-3">AE26781-Investment</h2>
        &nbsp;&nbsp;
        <div class="align-center justify-center">
          <v-btn color="primary">
            Select account
            <VIcon
              size="24"
              icon="ri-arrow-down-s-line"
            />
            <v-menu activator="parent">
              <v-list>
                <v-list-item>
                  <v-list-item-title>Your account 1</v-list-item-title>
                </v-list-item>
                <v-list-item>
                  <v-list-item-title>Your account 2</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>
          </v-btn>
        </div>
      </div>
      <div class="d-flex justify-center align-center">
        <h3 class="text-center pt-3">$100,231</h3>
      </div>
    </VCol>
    <VCol
      cols="12"
      md="6"
    >
      <ProfitLoss />
    </VCol>
    <VCol
      cols="12"
      md="6"
    >
      <AssetAllocation />
    </VCol>

    <VCol
      cols="12"
      md="12"
    >
      <VCard>
        <VTabs v-model="navigationTab">
          <VTab
            v-for="item in tabItems"
            :key="item"
            :value="item"
          >
            {{ item }}
          </VTab>
        </VTabs>

        <!-- tabs content -->
        <VWindow v-model="navigationTab">
          <VWindowItem value="Portfolio">
            <VRow>
              <VCol
                cols="6"
                md="6"
              >
                <IndustryPieCharts></IndustryPieCharts>
              </VCol>
              <VCol
                cols="6"
                md="6"
              >
                <PortfolioLineCharts></PortfolioLineCharts>
              </VCol>
              <VCol
                cols="12"
                md="12"
              >
                <PortfolioDetailsTable />
              </VCol>
            </VRow>
          </VWindowItem>
        </VWindow>
        <VWindow v-model="navigationTab">
          <VWindowItem value="Trading desk">
            <VRow>
              <VCol
                cols="12"
                md="12"
              >
                <LiquidCash></LiquidCash>
              </VCol>
              <VCol
                cols="12"
                md="12"
              >
                <LiquidCashTable />
              </VCol>
            </VRow>
          </VWindowItem>
        </VWindow>
      </VCard>
    </VCol>
  </VRow>
</template>
