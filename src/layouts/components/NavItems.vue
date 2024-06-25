<script setup>
import VerticalNavSectionTitle from '@/@layouts/components/VerticalNavSectionTitle.vue'
import VerticalNavGroup from '@layouts/components/VerticalNavGroup.vue'
import VerticalNavLink from '@layouts/components/VerticalNavLink.vue'
</script>

<template>
  <!-- 👉 Dashboards -->
  <VerticalNavGroup
    :item="{
      title: 'Dashboards',
      badgeContent: '5',
      badgeClass: 'bg-error',
      icon: 'ri-home-smile-line',
    }"
  >
    <VerticalNavLink
      :item="{
        title: 'Analytics',
        to: '/dashboard',
      }"
    />
  </VerticalNavGroup>

  <!-- 👉 Front Pages -->
  <VerticalNavGroup
    :item="{
      title: 'Front Pages',
      icon: 'ri-file-copy-line',
      badgeContent: 'Pro',
      badgeClass: 'bg-light-primary text-primary',
    }"
  >
    <VerticalNavLink
      :item="{
        title: 'Landing',
        href: 'https://demos.themeselection.com/materio-vuetify-vuejs-admin-template/demo-1/front-pages/landing-page',
        target: '_blank',
      }"
    />
  </VerticalNavGroup>
</template>
