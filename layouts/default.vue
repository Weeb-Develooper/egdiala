<template>
  <v-app :style="{ background: $vuetify.theme.themes.dark.background }">
    <v-navigation-drawer v-model="drawer" temporary app>
      <template v-slot:prepend>
        <v-list-item two-line>
          <v-list-item-avatar>
            <v-img src="/me1.jpg"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>Diala Egwuchukwu</v-list-item-title>
            <v-list-item-subtitle>Web Developer</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
      <v-container>
        <v-divider></v-divider>
      </v-container>
      <v-list shaped nav dense>
        <v-list-item-group active-class="indigo--text text--accent-3">
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :to="item.to"
            router
            exact
          >
            <v-list-item-action>
              <v-icon :color="item.color" dark>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app absolute color="transparent" dark flat> </v-app-bar>
    <v-main class="height-100">
      <nuxt />
    </v-main>

    <v-footer
      class="card-border"
      app
      dark
      padless
      :style="{ background: $vuetify.theme.themes.dark.background }"
    >
      <v-container>
        <v-row>
          <v-col cols="12" class="d-flex align-center secondary--text text-left"
            ><h3 class="font-weight-medium">
              Ⓒ Egwuchukwu Diala {{ new Date().getFullYear() }}
            </h3></v-col
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
      items: [
        {
          icon: 'mdi-18px mdi-home',
          title: 'Welcome',
          to: '/',
          color: 'indigo'
        },
        {
          icon: 'mdi-18px mdi-spin mdi-cog',
          title: 'Services',
          to: '/services',
          color: 'indigo'
        },
        {
          icon: 'mdi-18px mdi-package-variant-closed',
          title: 'Projects',
          to: '/projects',
          color: 'indigo'
        },
        {
          icon: 'mdi-18px mdi-account-details',
          title: 'About',
          to: '/about',
          color: 'indigo'
        }
      ],
      icons: [
        {
          icn: 'mdi-linkedin',
          url: 'https://www.linkedin.com/in/diala-egwuchukwu-006a33180/'
        },
        {
          icn: 'mdi-twitter',
          url: 'https://twitter.com/e_diala'
        },
        {
          icn: 'mdi-github',
          url: 'https://github.com/egdiala'
        },
        {
          icn: 'mdi-facebook',
          url: 'https://facebook.com/egwuchukwu'
        }
      ],
      title: 'Weeb Devel∞per'
    }
  },
  mounted() {
    this.$vuetify.theme.dark = true
    const theme = localStorage.getItem('useDarkTheme')
    if (theme) {
      if (theme === 'true') {
        this.$vuetify.theme.dark = true
        this.theme = 'mdi-white-balance-sunny'
      } else {
        this.$vuetify.theme.dark = false
        this.theme = 'mdi-moon-waxing-crescent'
      }
    } else {
      this.autoTheme()
    }
  },
  methods: {
    toggleTheme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark
      if (this.theme === 'mdi-moon-waxing-crescent') {
        this.theme = 'mdi-white-balance-sunny'
      } else {
        this.theme = 'mdi-moon-waxing-crescent'
      }
      localStorage.setItem('useDarkTheme', this.$vuetify.theme.dark.toString())
    },
    autoTheme() {
      const hours = new Date().getHours()
      if (hours <= 6 || hours >= 18) {
        this.$vuetify.theme.dark = true
        this.theme = 'mdi-white-balance-sunny'
      } else {
        this.$vuetify.theme.dark = false
        this.theme = 'mdi-moon-waxing-crescent'
      }
    }
  }
}
</script>

<style>
.height-100 {
  height: 100%;
}

.card-border {
  border: none;
}
</style>
