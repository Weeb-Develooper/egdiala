<template>
  <v-app :style="{ background: $vuetify.theme.themes.dark.background }">
    <v-app-bar app absolute color="transparent" dark flat> </v-app-bar>
    <v-main class="height-100">
      <nuxt />
    </v-main>

    <v-footer
      class="card-border"
      dark
      app
      absolute
      padless
      :style="{ background: $vuetify.theme.themes.dark.background }"
    >
      <v-container>
        <v-row>
          <v-col cols="12" class="d-flex align-center secondary--text text-left"
            ><h4 class="font-weight-medium">
              Ⓒ Egwuchukwu Diala {{ new Date().getFullYear() }}
            </h4></v-col
          >
        </v-row>
      </v-container>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      theme: '',
      title: 'Egwuchukwu S. Diala'
    }
  },
  mounted() {
    this.$vuetify.theme.dark = true
  },
  methods: {}
}
</script>

<style>
.height-100 {
  height: 100%;
}

.card-border {
  border: none;
  border-top-color: #000;
}
</style>
