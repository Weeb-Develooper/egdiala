<template>
  <v-container>
    <v-row
      class="fill-height d-flex flex-row justify-center align-center text-center"
    >
      <v-avatar size="100">
        <v-img src="/me1.jpg"></v-img>
      </v-avatar>

      <v-list-item>
        <v-list-item-content>
          <v-list-item-title>Diala Egwuchukwu</v-list-item-title>
          <v-list-item-subtitle>Web Developer</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-col cols="12" md="10" lg="4" class="mx-auto">
        <blockquote class="blockquote">
          &#8220;Hello! 👋 I’m a Fullstack Web Developer based in Lagos, Nigeria
          and I'm passionate about making the web accessible to everyone and
          building communities. I love making things that might possibly work
          using code. I've worked for 2 years as a web developer, and at points
          worked for tech firms in Nigeria.&#8221;
        </blockquote>
      </v-col>
    </v-row>

    <v-row
      class="fill-height d-flex flex-row justify-center align-center text-center"
    >
      <v-col cols="12" md="6">
        <h3 class="font-italic font-weight-medium">Experience Timeline</h3>
      </v-col>
    </v-row>

    <v-row
      class="fill-height d-flex flex-row justify-center align-center text-center"
    >
      <v-col cols="12" md="12" lg="11" class="text-md-center">
        <v-timeline v-resize="method1" :dense="dense">
          <v-timeline-item
            v-for="(year, i) in years"
            :key="i"
            :color="year.color"
            small
          >
            <template v-slot:opposite>
              <span
                :class="`headline font-weight-bold ${year.color}--text`"
                v-text="year.year"
              ></span>
            </template>
            <div class="py-4">
              <h2
                :class="`headline font-weight-light mb-4 ${year.color}--text`"
              >
                {{ year.title }}
              </h2>
              <div>{{ year.body }}</div>
            </div>
          </v-timeline-item>
        </v-timeline>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="6" md="3" lg="6">
        <v-btn
          href="https://github.com/egdiala/resume/raw/master/my-cv.pdf"
          target="_blank"
          tile
          outlined
          color="cyan"
          style="float: right;"
          dark
        >
          <v-icon left>mdi-file</v-icon>RÉSUMÉ
        </v-btn>
      </v-col>
      <v-col cols="6" md="3" lg="6">
        <v-btn
          href="https://github.com/egdiala/resume/raw/master/HngInternship%20(1).pdf"
          target="_blank"
          tile
          outlined
          color="success"
          style="float: left;"
          dark
          >HNGi 6.0</v-btn
        >
      </v-col>
    </v-row>

    <v-row
      class="fill-height d-flex flex-row justify-center align-center text-center"
    >
      <v-col cols="12" md="6">
        <h3 class="font-italic font-weight-medium">Contact</h3>
      </v-col>
    </v-row>

    <v-row class="fill-height d-flex flex-row justify-center align-center">
      <v-col cols="12" md="10" lg="5">
        <v-card class="mx-auto" raised tile>
          <v-list v-for="contact in contacts" :key="contact" two-line>
            <v-list-item
              v-if="contact.color"
              :href="contact.url"
              target="_blank"
            >
              <v-list-item-icon>
                <v-icon :color="contact.color" dark>{{ contact.icon }}</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title>{{ contact.title }}</v-list-item-title>
                <v-list-item-subtitle>{{ contact.sub }}</v-list-item-subtitle>
              </v-list-item-content>
              <v-list-item-icon>
                <v-icon :color="contact.colour">{{ contact.social }}</v-icon>
              </v-list-item-icon>
            </v-list-item>
            <v-divider
              v-else-if="contact.divider"
              :key="contact"
              :inset="contact.inset"
            ></v-divider>
          </v-list>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'About',

  data: () => ({
    reverse: true,
    dense: true,
    years: [
      {
        color: 'orange',
        year: '2020',
        title: 'WayaPayChat',
        body:
          "I got a job in WayaPayChat, a fintech company, on the 25th of July for the role of a frontend engineer. I'm currently developing their admin dashboard with VueJs which is used to manage their customers and show daily statistics and reporting. The experience has been amazing so far and I've been able to learn a lot and improve myself. Ps... I'm still a student 😏"
      },
      {
        color: 'cyan',
        year: '2019',
        title: 'SIWES',
        body:
          'I started my six months Internship on the 15th of July at Exood Technologies - a software company - located in Jibowu, Yaba, Lagos State. During the period of internship, I was exposed to new technologies, languages, concepts of problem solving and how to programmatically implement it.'
      },
      {
        color: 'green',
        year: '2019',
        title: 'HNGi 6.0',
        body:
          'During my six months SIWES, I took part in an online Internship organised by hotels.ng and finished as a Backend Developer. During the period of internship, I was exposed to new technologies, languages, concepts of problem solving and how to programmatically implement it. A certificate was also emailed to me as proof of participation. Click the HNGi 6.0 button below to download it.'
      }
    ],
    contacts: [
      {
        color: 'indigo',
        icon: 'mdi-phone',
        title: '+234 705 320 4002',
        sub: 'Mobile',
        social: 'mdi-whatsapp',
        url: 'https://wa.me/2347053204002',
        colour: 'green'
      },
      { divider: true, inset: true },
      {
        color: 'indigo',
        icon: 'mdi-message-text',
        title: 'dialaegwuchukwu@gmail.com',
        sub: 'Email',
        social: 'mdi-gmail',
        url: 'mailto:dialaegwuchukwu@gmail.com',
        colour: 'red'
      }
    ]
  }),
  mounted() {
    this.method1() // method1 will execute at pageload
  },
  methods: {
    method1() {
      const isMobile = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent)
      if (isMobile) {
        this.dense = true
      } else {
        this.dense = false
      }
    }
  },
  head() {
    return {
      title: 'About',
      meta: [
        {
          hid: 'description',
          name: 'about',
          content:
            'I’m a Fullstack Web Developer based in Lagos, Nigeria and I’m passionate about making the web accessible to everyone and building communities...'
        }
      ]
    }
  },
  inject: ['theme']
}
</script>
