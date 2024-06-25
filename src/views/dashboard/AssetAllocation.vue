<script setup>
import { useTheme } from 'vuetify'
import { hexToRgb } from '@layouts/utils'

const vuetifyTheme = useTheme()
const series = computed(() => {
  return [574, 103, 206] // Example data for pie chart
})

const chartOptions = computed(() => {
  const currentTheme = vuetifyTheme.current.value.colors
  const variableTheme = vuetifyTheme.current.value.variables

  return {
    chart: {
      parentHeightOffset: 0,
      toolbar: { show: false },
      type: 'pie', // Change chart type to pie
    },
    tooltip: { enabled: true }, // Enable tooltips for pie chart
    plotOptions: {
      pie: {
        dataLabels: {
          enabled: true,
        },
      },
    },
    colors: [currentTheme.error, currentTheme.success, currentTheme.warning],
    labels: ['Cash', 'Equity invested', 'Other assets'], // Example labels for pie chart
  }
})
</script>

<template>
  <VCard title="Asset Allocation">
    <VCardText class="pt-10">
      <VRow class="justify-center">
        <VueApexCharts
          type="pie"
          :options="chartOptions"
          :series="series"
          :height="400"
        />
      </VRow>
    </VCardText>
  </VCard>
</template>
