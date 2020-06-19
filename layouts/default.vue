<template>
  <v-app dark>
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
    <v-app-bar hide-on-scroll color="primary" app dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />

      <v-toolbar-title class="white--text" v-text="title" />
      <v-spacer />
      <v-btn icon @click="toggleTheme">
        <v-icon>{{ theme }}</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main>
      <nuxt />
    </v-main>

    <v-footer class="pa-0">
      <v-card
        flat
        tile
        width="100%"
        class="primary lighten-1 white--text text-center"
        dark
      >
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4 white--text"
            :href="icon.url"
            target="_blank"
            icon
          >
            <v-icon size="24px">{{ icon.icn }}</v-icon>
          </v-btn>
        </v-card-text>

        <v-container>
          <v-divider></v-divider>
        </v-container>

        <v-card-text class="white--text">
          © {{ new Date().getFullYear() }} |
          <strong>Weeb Devel∞per</strong>
        </v-card-text>
      </v-card>
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
