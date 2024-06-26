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
    title: 'Name',
    key: 'name',
  },
  {
    title: 'Type',
    key: 'type',
  },
  {
    title: 'Summary',
    key: 'summary1',
  },
  {
    title: 'Summary',
    key: 'summary2',
  },
]

const userData = [
  {
    id: 1,
    name: 'Report Q3 2024',
    type: 'earnings',
    summary1: 'xxxxxx',
    summary2: 'see details',
  },
  {
    id: 2,
    name: 'Report Q2 2024',
    type: 'earnings',
    summary1: 'xxxxxx',
    summary2: 'see details',
  },
  {
    id: 3,
    name: 'Report Q1 2024',
    type: 'earnings',
    summary1: 'xxxxxx',
    summary2: 'see details',
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
  <VDataTable
    :headers="headers"
    :items="userData"
    item-value="id"
    class="text-no-wrap"
  >
    <!-- Plan -->
    <template v-slot:item.summary2="{ item }">
      <router-link :to="'/accountreport'">
        <VBtn class="small">See details</VBtn>
      </router-link>
    </template>
    <template #bottom />
  </VDataTable>
</template>
