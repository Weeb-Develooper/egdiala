<template>
  <div>
    <v-overlay
      v-if="isLoading == true"
      :absolute="absolute"
      :opacity="opacity"
      :value="overlay"
      :z-index="zIndex"
    >
      <Splash />
    </v-overlay>

    <div v-else>
      <v-parallax src="/wall.jpg">
        <v-row class="fill-height d-flex flex-row justify-center align-center">
          <div class="container display-1 ml-5">
            I'm a
            <span
              ref="useTypedHere"
              class="orange--text text--lighten-3 typing"
            ></span>
          </div>
        </v-row>
      </v-parallax>

      <v-container>
        <v-row class="my-3 d-flex flex-row justify-center align-center">
          <v-icon>mdi-arrow-down</v-icon>
        </v-row>

        <v-row class="text-center">
          <v-col class="mb-4">
            <h1 class="display-2 font-weight-regular mb-3">What you get</h1>
            <v-lazy
              v-model="isActive"
              :options="{
                threshold: 0.5
              }"
              transition="fade-transition"
            >
              <p class="subheading font-weight-light">
                I deliver the best digital solutions suitable for your
                business/organization
              </p>
            </v-lazy>
          </v-col>
        </v-row>

        <v-row>
          <v-col v-for="card in cards" :key="card" cols="12" md="4">
            <v-lazy
              v-model="isActive"
              :options="{
                threshold: 0.5
              }"
              transition="fade-transition"
            >
              <v-card class="mx-auto" shaped hover>
                <v-img
                  class="white--text align-end"
                  height="210"
                  :src="`/${card.img.toLowerCase()}`"
                >
                  <v-card-title>{{ card.title }}</v-card-title>
                </v-img>

                <v-card-subtitle class="pb-0">{{
                  card.subTitle
                }}</v-card-subtitle>

                <v-card-text class="text--primary">
                  <div>{{ card.body }}</div>
                </v-card-text>

                <v-card-actions>
                  <v-btn small color="orange" to="/services" text>{{
                    card.btn
                  }}</v-btn>
                </v-card-actions>
              </v-card>
            </v-lazy>
          </v-col>
        </v-row>
      </v-container>

      <v-lazy
        v-model="isActive"
        :options="{
          threshold: 0.5
        }"
        transition="fade-transition"
      >
        <v-img src="/ferns.svg" height="550">
          <div
            class="container display-1 text-center fill-height d-flex flex-row justify-center align-center"
          >
            <div class="container last px-3 py-10 grey--text text--darken-1">
              <h3>SAY HELLO!</h3>
              <form
                name="contact"
                method="POST"
                data-netlify="true"
                data-netlify-honeypot="bot-field"
              >
                <input type="hidden" name="form-name" value="contact" />
                <v-row
                  class="d-flex flex-row justify-center align-center mx-5 my-5 pt-12"
                >
                  <v-col v-for="input in inputs" :key="input" cols="12" md="6">
                    <v-text-field
                      :type="input.type"
                      :name="input.name"
                      :label="input.label"
                      color="white"
                      class="my-n5"
                      dark
                      outlined
                    ></v-text-field>
                  </v-col>
                </v-row>
                <v-row
                  class="d-flex flex-row justify-center align-center mx-5 my-n10"
                >
                  <v-col cols="12">
                    <v-textarea
                      auto-grow
                      autocomplete="message"
                      color="white"
                      name="message"
                      label="Message"
                      dark
                      outlined
                    ></v-textarea>
                  </v-col>
                </v-row>
                <v-row
                  class="d-flex flex-row justify-center align-center mx-5 pt-12"
                >
                  <v-col cols="12" md="4">
                    <v-btn small block color="primary" type="submit" dark
                      >SEND</v-btn
                    >
                  </v-col>
                </v-row>
              </form>
            </div>
          </div>
        </v-img>
      </v-lazy>
    </div>
  </div>
</template>

<script>
import Typed from 'typed.js'
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
      cards: [
        {
          img: 'web-dev.jpg',
          title: 'Web Development',
          subTitle: 'JavaScript | PHP',
          body:
            'I build responsive and awesome user-experience and functional websites including web applications that drive growth and distinguishes your brand from other competitors.',
          btn: 'Explore'
        },
        {
          img: 'figma.png',
          title: 'UI/UX',
          subTitle: 'Figma',
          body:
            'I design fullscale web and mobile applications with prototyping to give you the feel of the actual product you need. I also design logos, flyers and branding for packages.',
          btn: 'Explore'
        },
        {
          img: 'mobileapp.png',
          title: 'Mobile App',
          subTitle: 'Flutter',
          body:
            'I create beautiful interface, responsive, awesome user-experience and functional mobile apps that drive growth and distinguishes your brand from other competitors.',
          btn: 'Explore'
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
      ]
    }
  },
  updated() {
    this.clickToUseTyped()
  },
  mounted() {
    setTimeout(() => {
      this.overlay = false
      this.isLoading = false
    }, 10000)
  },
  methods: {
    clickToUseTyped() {
      this.typed = new Typed(this.$refs.useTypedHere, {
        strings: [
          'Web Developer',
          'Vue Developer',
          'Nuxt Developer',
          'PHP Developer',
          'UI/UX Designer'
        ],
        typeSpeed: '10',
        backSpeed: '9',
        startDelay: '300',
        loop: 'true'
      })
    }
  },
  head() {
    return {
      title: 'Home',
      meta: [
        {
          hid: 'description',
          name: 'home',
          content: 'Welcome to my portfolio website.'
        }
      ]
    }
  }
}
</script>
