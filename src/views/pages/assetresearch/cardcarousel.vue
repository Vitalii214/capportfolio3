<template>
  <v-carousel
    height="300"
    hide-delimiters
  >
    <v-carousel-item
      v-for="(slide, i) in slides"
      :key="i"
    >
      <v-sheet height="100%">
        <div class="d-flex fill-height justify-center align-center">
          <v-row>
            <v-col
              cols="12"
              md="4"
            >
              <v-card
                height="250"
                class="ma-3"
              >
                <v-card-title>News title</v-card-title>
                <v-card-subtitle>
                  <div>(from website, scraped)</div>
                  <a>Link to open the news</a>
                </v-card-subtitle>
                <v-card-text>short description</v-card-text>
              </v-card>
            </v-col>
            <v-col
              cols="12"
              md="4"
            >
              <v-card
                height="250"
                class="ma-3"
              >
                <v-card-title>News title</v-card-title>
                <v-card-subtitle>
                  <div>(from website, scraped)</div>
                  <a>Link to open the news</a>
                </v-card-subtitle>
                <v-card-text>short description...</v-card-text>
              </v-card> </v-col
            ><v-col
              cols="12"
              md="4"
            >
              <v-card
                height="250"
                class="ma-3"
              >
                <v-card-title>News title</v-card-title>
                <v-card-subtitle>
                  <div>(from website, scraped)</div>
                  <a>Link to open the news</a>
                </v-card-subtitle>
                <v-card-text>short description...</v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
</template>
<script>
export default {
  data() {
    return {
      slides: ['First', 'Second', 'Third', 'Fourth', 'Fifth'],
    }
  },
}
</script>
