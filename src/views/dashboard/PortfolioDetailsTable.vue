<script setup>
import avatar1 from '@images/avatars/avatar-1.png'
import avatar2 from '@images/avatars/avatar-2.png'
import avatar3 from '@images/avatars/avatar-3.png'
import avatar4 from '@images/avatars/avatar-4.png'
import avatar5 from '@images/avatars/avatar-5.png'
import avatar6 from '@images/avatars/avatar-6.png'
import avatar7 from '@images/avatars/avatar-7.png'
import avatar8 from '@images/avatars/avatar-8.png'

const headers = [
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
]

const userData = [
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
]

const resolveUserRoleVariant = role => {
  const roleLowerCase = role.toLowerCase()
  if (roleLowerCase === 'subscriber')
    return {
      color: 'success',
      icon: 'ri-user-line',
    }
  if (roleLowerCase === 'author')
    return {
      color: 'error',
      icon: 'ri-computer-line',
    }
  if (roleLowerCase === 'maintainer')
    return {
      color: 'info',
      icon: 'ri-pie-chart-line',
    }
  if (roleLowerCase === 'editor')
    return {
      color: 'warning',
      icon: 'ri-edit-box-line',
    }
  if (roleLowerCase === 'admin')
    return {
      color: 'primary',
      icon: 'ri-vip-crown-line',
    }

  return {
    color: 'success',
    icon: 'ri-user-line',
  }
}

const resolveUserStatusVariant = stat => {
  const statLowerCase = stat.toLowerCase()
  if (statLowerCase === 'pending') return 'warning'
  if (statLowerCase === 'active') return 'success'
  if (statLowerCase === 'inactive') return 'secondary'

  return 'primary'
}
</script>

<template>
  <VCard title="Portfolio details">
    <VDataTable
      :headers="headers"
      :items="userData"
      item-value="id"
      class="text-no-wrap"
    >
      <!-- User -->
      <template #item.username="{ item }">
        <div class="d-flex align-center gap-x-4">
          <VAvatar
            size="34"
            :variant="!item.avatar ? 'tonal' : undefined"
            :color="!item.avatar ? resolveUserRoleVariant(item.role).color : undefined"
          >
            <VImg
              v-if="item.avatar"
              :src="item.avatar"
            />
          </VAvatar>

          <div class="d-flex flex-column">
            <h6 class="text-h6 font-weight-medium user-list-name">
              {{ item.fullName }}
            </h6>

            <span class="text-sm text-medium-emphasis">@{{ item.username }}</span>
          </div>
        </div>
      </template>
      <!-- Role -->
      <template #item.role="{ item }">
        <div class="d-flex gap-4">
          <VIcon
            :icon="resolveUserRoleVariant(item.role).icon"
            :color="resolveUserRoleVariant(item.role).color"
            size="22"
          />
          <div class="text-capitalize text-high-emphasis">
            {{ item.role }}
          </div>
        </div>
      </template>
      <!-- Plan -->
      <template #item.plan="{ item }">
        <span class="text-capitalize text-high-emphasis">{{ item.currentPlan }}</span>
      </template>
      <!-- Status -->
      <template #item.status="{ item }">
        <VChip
          :color="resolveUserStatusVariant(item.status)"
          size="small"
          class="text-capitalize"
        >
          {{ item.status }}
        </VChip>
      </template>

      <template #bottom />
    </VDataTable>
  </VCard>
</template>
