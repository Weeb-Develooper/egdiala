<template>
  <v-container class="height-100 d-flex align-center">
    <v-overlay
      v-if="isLoading"
      :absolute="absolute"
      :opacity="opacity"
      :value="overlay"
      :z-index="zIndex"
    >
      <Splash />
    </v-overlay>

    <v-row
      v-else
      class="height-100 d-flex align-center align-content-space-around justify-space-between flex-wrap"
    >
      <v-col cols="12" xl="5" lg="5" class="d-flex align-center">
        <v-lazy
          v-model="isActive"
          :options="{
            threshold: 0.5
          }"
          transition="scroll-x-transition"
        >
          <div class="text-left">
            <h3 class="headline font-weight-medium">
              Egwuchukwu S. Diala
            </h3>
            <h3 class="subtitle-2 font-weight-medium secondary--text">
              VueJs Developer
            </h3>
            <br />
            <blockquote>
              &#8220;Hello! 👋🏾 I’m a Frontend Engineer based in Lagos, Nigeria
              and I'm passionate about making the web accessible to everyone and
              building communities. I love making things that might possibly
              work using code. I've worked for 2 years as a frontend developer
              and UI developer. I have hands-on experience working with Vue,
              Vuex, Vue Router and Nuxt.&#8221;
            </blockquote>
            <br />
            <v-row class="d-flex justify-left">
              <a
                v-for="(link, i) in links"
                :key="i"
                :href="link.url"
                class="headline mx-3 d-flex align-center"
                target="_blank"
              >
                <span
                  class="iconify"
                  :style="`color: ${link.color};`"
                  :data-icon="`simple-icons:${link.dataIcon}`"
                  data-inline="false"
                ></span>
              </a>
              <v-dialog transition="slide-y-transition" max-width="600">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    class="ml-auto mx-3 text-capitalize"
                    color="green"
                    v-bind="attrs"
                    text
                    plain
                    :ripple="false"
                    v-on="on"
                  >
                    Hire me
                  </v-btn>
                </template>
                <template v-slot:default="dialog">
                  <v-card>
                    <form
                      name="contact"
                      method="POST"
                      data-netlify="true"
                      data-netlify-honeypot="bot-field"
                    >
                      <v-toolbar color="primary" class="subtitle-1" dark>
                        Get in touch! 😁
                        <v-icon
                          class="ml-auto mx-3"
                          plain
                          :ripple="false"
                          text
                          @click="dialog.value = false"
                        >
                          mdi-close
                        </v-icon>
                      </v-toolbar>
                      <v-card-text>
                        <input type="hidden" name="form-name" value="contact" />
                        <v-row>
                          <v-col cols="12">
                            <v-text-field
                              v-for="(input, k) in inputs"
                              :key="k"
                              :type="input.type"
                              :name="input.name"
                              :label="input.label"
                              color="white"
                              dark
                              dense
                              outlined
                            ></v-text-field>
                            <v-textarea
                              auto-grow
                              autocomplete="message"
                              color="white"
                              name="message"
                              label="Message"
                              dark
                              dense
                              outlined
                            ></v-textarea>
                            <v-btn
                              type="submit"
                              block
                              :ripple="false"
                              color="green"
                              >SEND</v-btn
                            >
                          </v-col>
                        </v-row>
                      </v-card-text>
                    </form>
                  </v-card>
                </template>
              </v-dialog>
            </v-row>
          </div>
        </v-lazy>
      </v-col>

      <v-col cols="12" xl="6" lg="6">
        <v-lazy
          v-model="isActive"
          :options="{
            threshold: 0.5
          }"
          transition="fade-transition"
        >
          <div class="text-center mx-auto">
            <h1 class="text-h5 font-weight-medium">
              Projects
            </h1>
            <v-virtual-scroll
              :bench="benched"
              :items="items"
              height="360"
              item-height="125"
              class="hide my-2"
            >
              <template v-slot:default="{ item, m }">
                <v-card :key="m" class="project-card" min-width="344">
                  <v-card-title>
                    {{ item.title }}
                  </v-card-title>

                  <v-card-actions>
                    <v-btn
                      v-if="item.live"
                      :href="item.live"
                      target="_blank"
                      link
                      small
                      class="font-weight-light"
                      color="orange"
                      text
                    >
                      View
                    </v-btn>
                    <v-btn
                      v-if="item.source"
                      :href="item.source"
                      target="_blank"
                      link
                      small
                      class="font-weight-light"
                      color="blue"
                      text
                    >
                      GitHub
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </template>
            </v-virtual-scroll>
            <v-icon class="down" color="white">mdi-arrow-down</v-icon>
          </div>
        </v-lazy>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Splash from '~/components/splash.vue'
export default {
  components: { Splash },
  data() {
    return {
      absolute: false,
      opacity: 1,
      overlay: true,
      zIndex: 5,
      typed: null,
      isActive: false,
      isLoading: true,
      benched: 0,
      links: [
        {
          url: 'https://www.linkedin.com/in/diala-egwuchukwu-006a33180',
          dataIcon: 'linkedin',
          color: '#0A66C2'
        },
        {
          url: 'https://github.com/egdiala',
          dataIcon: 'github',
          color: '#ffffff'
        },
        {
          url: 'https://twitter.com/e_diala?s=09',
          dataIcon: 'twitter',
          color: 'rgba(29,161,242,1.00)'
        }
      ],
      inputs: [
        {
          type: 'text',
          name: 'name',
          label: 'Name'
        },
        {
          type: 'email',
          name: 'email',
          label: 'Email'
        }
      ],
      projects: [
        {
          title: 'QLIP',
          live: 'https://qlipit.io',
          source: 'https://github.com/egdiala/qlip'
        },
        {
          title: 'My Portfolio',
          source: 'https://github.com/Weeb-Develooper/egdiala'
        },
        {
          title: 'OtakonTitan',
          live: 'https://otakontitan.netlify.app',
          source: 'https://github.com/egdiala/otakontitan'
        },
        {
          title: "Wendy's Portfolio",
          live: 'https://wendywu.netlify.app',
          source: 'https://github.com/Weeb-Develooper/egdiala'
        },
        {
          title: 'Music Parrot',
          live: 'https://musicparrot.netlify.app',
          source: 'https://github.com/egdiala/music-parrot'
        },
        {
          title: 'News App',
          source: 'https://github.com/egdiala/news-app'
        }
      ]
    }
  },
  computed: {
    items() {
      const projects = this.projects
      // const projectsLength = this.projects.length

      return projects
    }
  },
  created() {
    setTimeout(() => {
      this.isLoading = false
      this.overlay = false
    }, 5000)
  },
  methods: {
    random(min, max) {
      return Math.floor(Math.random() * (max - min)) + min
    }
  },
  head() {
    return {
      title: 'Egwuchukwu S. Diala'
    }
  }
}
</script>

<style scoped>
::-webkit-scrollbar {
  display: none;
}

@keyframes float {
  0% {
    box-shadow: 0 5px 15px 0px rgba(0, 0, 0, 0.6);
    transform: translatey(0px);
  }
  50% {
    box-shadow: 0 25px 15px 0px rgba(0, 0, 0, 0.2);
    transform: translatey(-10px);
  }
  100% {
    box-shadow: 0 5px 15px 0px rgba(0, 0, 0, 0.6);
    transform: translatey(0px);
  }
}

.down {
  transform: translatey(0px);
  animation: float 2s ease-in-out infinite;
}

.project-card {
  border-radius: 8px !important;
}
</style>
