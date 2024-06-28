<script setup>
import NavItems from '@/layouts/components/NavItems.vue'
import logo from '@images/logo.svg?raw'
import VerticalNavLayout from '@layouts/components/VerticalNavLayout.vue'
import Footer from '@/layouts/components/Footer.vue'
import NavbarThemeSwitcher from '@/layouts/components/NavbarThemeSwitcher.vue'
import UserProfile from '@/layouts/components/UserProfile.vue'
</script>

<template>
  <VerticalNavLayout>
    <!-- 👉 navbar -->
    <template #navbar="{ toggleVerticalOverlayNavActive }">
      <div class="d-flex h-100 align-center">
        <div
          class="d-flex align-center cursor-pointer"
          style="user-select: none"
        >
          <span class="d-none d-md-flex align-center text-disabled">
            <v-btn @click="toggleVerticalOverlayNavActive(true)">Open AI Assistant</v-btn>
          </span>
        </div>

        <VSpacer />

        <NavbarThemeSwitcher class="me-2" />

        <UserProfile />
      </div>
    </template>

    <template #vertical-nav-header="{ toggleIsOverlayNavActive }"
      ><v-row>
        <v-col
          ><div class="d-flex justify-space-between align-center">
            <div><h1 class="font-weight-medium leading-normal text-xl text-uppercase">Portfolio Assistant</h1></div>
            &nbsp;&nbsp;&nbsp;&nbsp;
            <IconBtn
              class="d-block d-lg-none justify-end"
              @click="toggleIsOverlayNavActive(false)"
            >
            
              <VIcon icon="ri-close-line" />
            </IconBtn></div></v-col
        >
      </v-row>
    </template>

    <template #vertical-nav-content>
      <NavItems />
    </template>
    <!-- 👉 Pages -->
    <slot />
  </VerticalNavLayout>
</template>

<style lang="scss" scoped>
.meta-key {
  border: thin solid rgba(var(--v-border-color), var(--v-border-opacity));
  border-radius: 6px;
  block-size: 1.5625rem;
  line-height: 1.3125rem;
  padding-block: 0.125rem;
  padding-inline: 0.25rem;
}

.app-logo {
  display: flex;
  align-items: center;
  column-gap: 0.75rem;

  .app-logo-title {
    font-size: 1.25rem;
    font-weight: 500;
    line-height: 1.75rem;
    text-transform: uppercase;
  }
}
</style>
