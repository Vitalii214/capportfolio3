<script setup>
import { useTheme } from 'vuetify'
import { hexToRgb } from '@layouts/utils'

const vuetifyTheme = useTheme()
const series = computed(() => {
  return [20000, 10000, 15000, 43000] // Example data for pie chart
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
          formatter: function (val) {
            return val.toFixed(0) // Format data labels to two decimal places
          },
        },
      },
    },
    grid: { show: false }, // Hide grid for pie chart
    colors: [currentTheme.error, currentTheme.success, currentTheme.warning, currentTheme.primary],
    stroke: { show: false }, // No stroke needed for pie chart
    labels: ['Finance', 'HLS', 'Retail', 'Energy'], // Example labels for pie chart
  }
})
</script>

<template>
  <VCard title="Industry Pie Chart">
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
