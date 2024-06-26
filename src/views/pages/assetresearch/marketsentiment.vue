<template>
    <v-card
      ref="chartContainer"
      class="chart-container"
    >
      <v-card-text class="pt-10">
        <vue-apex-charts
          ref="apexChart"
          type="line"
          :options="chartOptions"
          :series="series"
          :height="chartHeight"
        />
      </v-card-text>
    </v-card>
  </template>
  
  <script setup>
  import { useTheme } from 'vuetify'
  import { ref, computed, onMounted, onUnmounted } from 'vue'
  import VueApexCharts from 'vue3-apexcharts'
  import { hexToRgb } from '@layouts/utils'
  
  const vuetifyTheme = useTheme()
  
  // Example data for line chart
  const series = computed(() => [
    {
      name: 'Series 1',
      data: [30, 40, 35, 50, 49, 60, 70, 91, 125],
    },
  ])
  
  // Chart options
  const chartOptions = computed(() => {
    const currentTheme = vuetifyTheme.value?.currentTheme?.colors || {}
    const variableTheme = vuetifyTheme.value?.currentTheme?.variables || {}
  
    return {
      chart: {
        type: 'line',
        parentHeightOffset: 0,
        toolbar: {
          show: false,
        },
      },
      tooltip: {
        enabled: true,
      },
      grid: {
        // borderColor: `rgba(${hexToRgb(String(variableTheme['border-color']))},${variableTheme['border-opacity']})`,
        borderColor: '#eee',
        strokeDashArray: 6,
        xaxis: {
          lines: {
            show: true,
          },
        },
        yaxis: {
          lines: {
            show: true,
          },
        },
        padding: {
          top: -10,
          left: -7,
          right: 5,
          bottom: 5,
        },
      },
      colors: ['#FF5733'],
      markers: {
        size: 6,
        offsetY: 4,
        offsetX: -2,
        strokeWidth: 3,
        colors: ['#FF5733'],
        strokeColors: '#FF5733',
        discrete: [
          {
            size: 5.5,
            seriesIndex: 0,
            strokeColor: '#FF5733',
            fillColor: '#FF5733',
            dataPointIndex: series.value[0].data.length - 1,
          },
        ],
        hover: {
          size: 7,
        },
      },
      xaxis: {
        categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep'],
      },
      yaxis: {
        labels: {
          show: true,
        },
      },
    }
  })
  
  // Dynamic chart height based on parent container
  const chartHeight = ref(400) // Initial height
  
  // Watch for resize events to update chart dimensions
  const resizeChart = () => {
    chartHeight.value = Math.min(
      400,
      Math.max(200, window.innerHeight * 0.6), // Adjust as needed based on your layout and design
    )
  }
  
  onMounted(() => {
    // Initialize chart height
    resizeChart()
  
    // Listen for window resize events
    window.addEventListener('resize', resizeChart)
  })
  
  onUnmounted(() => {
    // Clean up resize event listener
    window.removeEventListener('resize', resizeChart)
  })
  </script>
  
  <style scoped>
  .chart-container {
    width: 100%; /* Ensure the chart container takes full width */
  }
  </style>
  