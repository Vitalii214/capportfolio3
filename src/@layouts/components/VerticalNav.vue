<script setup>
import { PerfectScrollbar } from 'vue3-perfect-scrollbar'
import { useDisplay } from 'vuetify'
import logo from '@images/logo.svg?raw'

const props = defineProps({
  tag: {
    type: null,
    required: false,
    default: 'aside',
  },
  isOverlayNavActive: {
    type: Boolean,
    required: true,
  },
  toggleIsOverlayNavActive: {
    type: Function,
    required: true,
  },
})

const { mdAndDown } = useDisplay()
const refNav = ref()



/*ℹ️ Close overlay side when route is changed
Close overlay vertical nav when link is clicked
*/
const route = useRoute()

watch(
  () => route.path,
  () => {
    props.toggleIsOverlayNavActive(false)
  },
)

const isVerticalNavScrolled = ref(false)
const updateIsVerticalNavScrolled = val => (isVerticalNavScrolled.value = val)

const handleNavScroll = evt => {
  isVerticalNavScrolled.value = evt.target.scrollTop > 0
}
</script>

<template>
  <!-- eslint-disable vue/no-v-html -->
  <Component
    :is="props.tag"
    ref="refNav"
    :width="500"
    class="layout-vertical-nav"
    :class="[
      {
        visible: isOverlayNavActive,
        scrolled: isVerticalNavScrolled,
        'overlay-nav': mdAndDown,
      },
    ]"
  >
    <!-- 👉 Header -->
    <div class="nav-header">
      <slot name="nav-header"> </slot>
    </div>
    <slot name="before-nav-items"> </slot>
    <slot
      name="nav-items"
      :update-is-vertical-nav-scrolled="updateIsVerticalNavScrolled"
    >
     
      <div class="d-flex flex-column">
        <v-row>
          <v-col
            md="12"
            cols="12"
            ><v-card
              class="ma-2 w-250"
              flat
              style="height: 300px; overflow-y: auto"
            >
              <v-row justify="end"
                ><v-col
                  cols="12"
                  md="8"
                  class="mt-2"
                  ><v-alert
                    border="end"
                    density="compact"
                    border-color="deep-purple accent-4"
                    elevation="2"
                  >
                    answer
                  </v-alert></v-col
                ></v-row
              >
              <v-row
                ><v-col
                  cols="12"
                  md="8"
                  ><v-alert
                    border="start"
                    border-color="deep-purple accent-4"
                    elevation="2"
                    density="compact"
                  >
                    ______sentiment is .
                  </v-alert></v-col
                ></v-row
              >
              <v-row justify="end"
                ><v-col
                  cols="12"
                  md="8"
                  ><v-alert
                    border="end"
                    density="compact"
                    border-color="deep-purple accent-4"
                    elevation="2"
                  >
                    answer
                  </v-alert></v-col
                ></v-row
              >
              <v-row
                ><v-col
                  cols="12"
                  md="8"
                  ><v-alert
                    border="start"
                    border-color="deep-purple accent-4"
                    elevation="2"
                    density="compact"
                  >
                    Buy 10 shares of apple
                  </v-alert></v-col
                ></v-row
              ><v-row justify="end"
                ><v-col
                  cols="12"
                  md="10"
                >
                  <v-alert
                    border="end"
                    border-color="deep-purple accent-4"
                    elevation="2"
                    density="compact"
                  >
                    <h3 class="text-center pt-3">AE26781-Investment</h3>
                    <v-divider></v-divider>
                    <span
                      >I understand you want me to place an order for AAPL at current market place for 10 shares. Please
                      confirm</span
                    >
                  </v-alert>
                </v-col></v-row
              >
              <v-row
                ><v-col
                  cols="12"
                  md="6"
                  class="d-flex align-center justify-center"
                  ><router-link :to="'/assetresearch'">
                    <v-btn color="success">Buy 10 shares</v-btn>
                  </router-link> </v-col
                ><v-col
                  cols="12"
                  md="6"
                  class="d-flex align-center justify-center"
                  ><v-btn color="error">Cancel</v-btn>
                </v-col></v-row
              >
            </v-card></v-col
          >
        </v-row>
        <v-row class="d-flex justify-center align-center">
          <v-col
            md="9"
            cols="12"
            class="ml-1"
            ><v-text-field
              clearable
              label="Ask question"
            ></v-text-field
          ></v-col>
          <v-col
            md="2"
            cols="12"
            ><v-btn>Send</v-btn></v-col
          >
        </v-row>

        <v-row class="ma-1">
          <v-col
            class="mt-3"
            cols="12"
            md="12"
            >Sample questions</v-col
          >
          <v-col
            cols="12"
            md="12"
            class="d-flex"
            ><v-btn
              block
              class="align-center justify-center"
              >Initiate Transaction</v-btn
            ></v-col
          ><v-col
            cols="12"
            md="12"
            class="d-flex"
            ><v-btn
              block
              class="align-center justify-center"
              >Summarize market sentiment around AAPL</v-btn
            ></v-col
          ><v-col
            cols="12"
            md="12"
            class="d-flex"
            ><v-btn
              block
              class="align-center justify-center"
              >Give me a summary of APPL Q3 fnancial report</v-btn
            ></v-col
          ></v-row
        >
      </div>
      <PerfectScrollbar
        tag="ul"
        class="nav-items"
        :options="{ wheelPropagation: false }"
        @ps-scroll-y="handleNavScroll"
      >
        <slot />
      </PerfectScrollbar>
    </slot>

    <slot name="after-nav-items" />
  </Component>
</template>

<style lang="scss" scoped>
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
.nav-header {
  background-color: red($color: #000000);
}
</style>

<style lang="scss">
@use '@configured-variables' as variables;
@use '@layouts/styles/mixins';

// 👉 Vertical Nav
.layout-vertical-nav {
  position: fixed;
  z-index: variables.$layout-vertical-nav-z-index;
  display: flex;
  flex-direction: column;
  block-size: 100%;
  inline-size: variables.$layout-vertical-nav-width;
  inset-block-start: 0;
  inset-inline-start: 0;
  transition: inline-size 0.25s ease-in-out, box-shadow 0.25s ease-in-out;
  will-change: transform, inline-size;
  width: 400px;
  background-color: rgb(190, 115, 17);
  .nav-header {
    display: flex;
    align-items: center;
    background-color: aliceblue;
    .header-action {
      cursor: pointer;

      @at-root {
        #{variables.$selector-vertical-nav-mini} .nav-header .header-action {
          &.nav-pin,
          &.nav-unpin {
            display: none !important;
          }
        }
      }
    }
  }

  .app-title-wrapper {
    margin-inline-end: auto;
  }

  .nav-items {
    block-size: 100%;

    // ℹ️ We no loner needs this overflow styles as perfect scrollbar applies it
    // overflow-x: hidden;

    // // ℹ️ We used `overflow-y` instead of `overflow` to mitigate overflow x. Revert back if any issue found.
    // overflow-y: auto;
  }

  .nav-item-title {
    overflow: hidden;
    margin-inline-end: auto;
    text-overflow: ellipsis;
    white-space: nowrap;
  }

  // 👉 Collapsed
  .layout-vertical-nav-collapsed & {
    &:not(.hovered) {
      inline-size: variables.$layout-vertical-nav-collapsed-width;
    }
  }
}

// Small screen vertical nav transition
@media (max-width: 1279px) {
  .layout-vertical-nav {
    &:not(.visible) {
      transform: translateX(-#{variables.$layout-vertical-nav-width});

      @include mixins.rtl {
        transform: translateX(variables.$layout-vertical-nav-width);
      }
    }

    transition: transform 0.25s ease-in-out;
  }
}
</style>
