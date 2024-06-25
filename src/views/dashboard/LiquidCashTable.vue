<template>
  <v-card flat>
    <template v-slot:text>
      <v-text-field
        v-model="search"
        label="Asset Search"
        prepend-inner-icon="mdi-magnify"
        variant="outlined"
        hide-details
        single-line
      ></v-text-field>
    </template>

    <v-data-table
      :headers="headers"
      :items="desserts"
      :search="search"
    >
      <template v-slot:item.last15day="{ item }">
        <Last15DayChart></Last15DayChart>
      </template>
      <template v-slot:item.details="{ item }">
        <VBtn class="small">See details</VBtn>
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
import { VBtn } from 'vuetify/lib/components/index.mjs';
import Last15DayChart from './Last15DayCharts.vue'
export default {
  data() {
    return {
      search: '',
      headers: [
        {
          title: 'Company name',
          key: 'companyname',
        },
        {
          title: 'ticker',
          key: 'ticker',
        },
        {
          title: 'Industry',
          key: 'industry',
        },
        {
          title: 'MarketCa',
          key: 'marketca',
        },
        {
          title: 'Share number',
          key: 'sharenum',
        },
        {
          title: 'Share price',
          key: 'shareprice',
        },
        {
          title: 'Value',
          key: 'value',
        },
        {
          title: 'Last 15day',
          key: 'last15day',
        },
        {
          title: 'Last month',
          key: 'lastmonth',
        },
        {
          title: 'Details',
          key: 'details',
        },
      ],
      desserts: [
        {
          id: 1,
          companyname: 'Apple',
          ticker: 'AAPL',
          industry: 'tech',
          marketca: '12B',
          sharenum: '12',
          shareprice: '$100',
          value: '$12',
          last15day: '+12%',
          lastmonth: '+15%',
          details: 'Sent',
        },
        {
          id: 2,
          companyname: 'Google',
          ticker: 'GOO',
          industry: 'tech',
          marketca: '12B',
          sharenum: '12',
          shareprice: '$100',
          value: '$12',
          last15day: '+12%',
          lastmonth: '+15%',
          details: 'Sent',
        },
        {
          id: 3,
          companyname: 'EcoGreen',
          ticker: 'EGR',
          industry: 'energy',
          marketca: '5B',
          sharenum: '8',
          shareprice: '$50',
          value: '$55',
          last15day: '+10%',
          lastmonth: '+15%',
          details: 'Sent',
        },
        {
          id: 4,
          companyname: 'TranspoLog',
          ticker: 'TLOG',
          industry: 'transportation',
          marketca: '10B',
          sharenum: '9',
          shareprice: '$60',
          value: '$66',
          last15day: '+10%',
          lastmonth: '+12%',
          details: 'Sent',
        },
      ],
    }
  },
  components: {
    Last15DayChart,
  },
}
</script>
