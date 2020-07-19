<template>
  <div>
    <v-container>
      <v-row
        v-for="project in projects"
        :key="project"
        class="justify-center align-center"
      >
        <v-col cols="12">
          <v-lazy
            v-model="isActive"
            :options="{
              threshold: 0.5
            }"
            transition="fade-transition"
          >
            <v-sheet :color="project.sheet" rounded>
              <v-col cols="12" md="10" lg="6" class="mx-auto">
                <v-card hover="true">
                  <v-carousel
                    :continuous="true"
                    :cycle="true"
                    :show-arrows="false"
                    delimiter-icon="mdi-minus"
                    height="300"
                    dark
                  >
                    <v-carousel-item
                      v-for="pic in project.src"
                      :key="pic"
                      :src="`/${pic.img.toLowerCase()}.png`"
                      dark
                    ></v-carousel-item>
                  </v-carousel>

                  <v-card-title class="pb-0">{{ project.name }}</v-card-title>

                  <v-card-text class="text--primary">
                    <div class="font-weight-light">{{ project.title }}</div>

                    <div>{{ project.text }}</div>
                  </v-card-text>
                  <v-divider class="mx-4"></v-divider>

                  <v-card-text>
                    <v-col cols="12" md="12" lg="12">
                      <v-chip
                        v-for="tech in project.techs"
                        :key="tech"
                        :color="tech.color"
                        text-color="white"
                        small
                        class="ma-2"
                        >{{ tech.name }}</v-chip
                      >
                    </v-col>
                  </v-card-text>

                  <v-card-actions>
                    <v-btn
                      v-if="project.live"
                      color="orange"
                      text
                      :href="project.live"
                      target="_blank"
                      >LIVE</v-btn
                    >

                    <v-btn
                      v-if="project.git"
                      color="orange"
                      text
                      :href="project.git"
                      target="_blank"
                      >GitHub</v-btn
                    >
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-sheet>
          </v-lazy>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Projects',

  data: () => ({
    projects: [
      {
        src: [
          {
            img: 'classroom'
          },
          {
            img: 'classroom1'
          },
          {
            img: 'classroom2'
          }
        ],
        name: 'Mini Classroom Application',
        title: 'by Team Dollar, HNG 6.0',
        sheet: 'pink lighten-2',
        live: 'https://alvdeenservices.000webhostapp.com/',
        git: 'https://github.com/egdiala/Team-Dollar-Mini-Classroom',
        text:
          'This is a mini classroom web application developed as a project with other team members during my online internship at HNG.',
        techs: [
          {
            name: 'Bootstrap',
            color: 'purple darken-3'
          },
          {
            name: 'PHP',
            color: 'indigo lighten-1'
          },
          {
            name: 'SQL',
            color: 'red'
          }
        ]
      },
      {
        src: [{ img: 'waybill' }, { img: 'waybill1' }, { img: 'waybill2' }],
        name: 'Invoice Generator',
        title: 'by Weeb Develooper',
        sheet: 'orange lighten-2',
        live: 'https://ittjwims.000webhostapp.com/',
        git: 'https://github.com/egdiala/invoice-generator',
        text:
          'This is an invoice generator done by me. The software keeps track of sales done and can print and also reprint invoices for any transaction made. I also used javascript to convert the numbers to words when calculating price of products.',
        techs: [
          {
            name: 'Bootstrap',
            color: 'purple darken-3'
          },
          {
            name: 'PHP',
            color: 'indigo lighten-1'
          },
          {
            name: 'SQL',
            color: 'red'
          },
          {
            name: 'JavaScript',
            color: 'yellow'
          },
          {
            name: 'JQuery',
            color: 'indigo'
          }
        ]
      },
      {
        src: [
          { img: 'socialape' },
          { img: 'socialape1' },
          { img: 'socialape2' }
        ],
        name: 'Social App',
        title: 'by Weeb Develooper',
        sheet: 'blue lighten-2',
        live: 'https://socialape-5c0f6.firebaseapp.com/',
        git: 'https://github.com/egdiala/socialape-react',
        text:
          'This is a social web application done by me as a project given by my lecturer in school.',
        techs: [
          {
            name: 'Material UI',
            color: 'blue darken-2'
          },
          {
            name: 'Node Js',
            color: 'green'
          },
          {
            name: 'React',
            color: 'blue lighten-1'
          },
          {
            name: 'Firebase',
            color: 'orange darken-5'
          }
        ]
      },
      {
        src: [
          {
            img: 'uiux'
          },
          {
            img: 'uiux1'
          },
          {
            img: 'uiux2'
          },
          {
            img: 'uiux3'
          }
        ],
        name: 'Movie App Design',
        title: 'by Weeb Develooper',
        sheet: 'brown lighten-2',
        live: 'https://www.figma.com/file/21RGoly39iZZhcwlGXCDGW/Voozie',
        text:
          'This is a UI/UX design for a movie streaming mobile application.',
        techs: [
          {
            name: 'Figma',
            color: 'blue'
          }
        ]
      }
    ]
  }),
  head() {
    return {
      title: 'Projects',
      meta: [
        {
          hid: 'description',
          name: 'projects',
          content: 'Works done by me.'
        }
      ]
    }
  }
}
</script>
