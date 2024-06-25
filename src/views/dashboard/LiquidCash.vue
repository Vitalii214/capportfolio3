<script setup>
import { useTheme } from 'vuetify'
import DropDownList from './DropDownList.vue';

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
    tooltip: { enabled: false }, // Enable tooltips for pie chart
    plotOptions: {
      pie: {
        dataLabels: {
          enabled: true,
          formatter: function (val) {
            return val.toFixed(2) // Format data labels to two decimal places
          },
        },
      },
    },
    grid: { show: false }, // Hide grid for pie chart
    colors: [currentTheme.error, currentTheme.success, currentTheme.warning],
    stroke: { show: false }, // No stroke needed for pie chart
    labels: ['Cash', 'Equity invested', 'Other assets'], // Example labels for pie chart
  }
})
</script>

<template>
  <VCard>
    <VCardText class="pt-10">
      <div class="d-flex align-center pl-5">
        <h3 class="text-h3">Liquid Cash Available</h3>&nbsp;&nbsp;
        <h1 class="text-h1">$10,123</h1>
      </div>
      <div>
        <DropDownList></DropDownList>
      </div>
    </VCardText>
  </VCard>
</template>
