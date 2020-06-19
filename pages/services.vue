<template>
  <v-container>
    <v-row
      class="fill-height d-flex flex-row justify-center align-center text-center"
    >
      <v-col cols="12" md="6">
        <h3 class="headline font-italic font-weight-medium">My Services</h3>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" md="4" v-for="card in cards" :key="card">
        <v-card
          class="mx-auto"
          max-width="360"
          min-height="410"
          outlined
          raised
          shaped
          tile
        >
          <v-list-item three-line>
            <v-list-item-content>
              <div class="overline mb-4" style="float: left;">
                <v-icon>{{ card.icon }}</v-icon>
              </div>
              <v-list-item-title class="headline mb-1">
                {{ card.title }}
              </v-list-item-title>
            </v-list-item-content>

            <v-list-item-avatar tile size="100" color="grey">
              <v-img
                :src="`/${card.img.toLowerCase()}`"
                aspect-ratio="1.5"
              ></v-img>
            </v-list-item-avatar>
          </v-list-item>
          <v-card-text>{{ card.text }}</v-card-text>

          <v-card-actions>
            <v-col cols="12" md="12" lg="12">
              <v-chip
                v-for="skill in card.skills"
                :key="skill"
                small
                class="ma-2"
                :color="skill.color"
                text-color="white"
                >{{ skill.skill1 }}</v-chip
              >
            </v-col>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Services',
  head() {
    return {
      title: 'Services',
      meta: [
        {
          hid: 'description',
          name: 'services',
          content: 'My skillset'
        }
      ]
    }
  },

  data: () => ({
    cards: [
      {
        icon: 'mdi-code-tags',
        title: 'Web Development',
        img: 'web_dev.jpg',
        text:
          'I build responsive and functional web applications that help clients increase customer/visitor engagement.',
        skills: [
          { skill1: 'HTML5', color: 'deep-orange darken-1' },
          { skill1: 'CSS', color: 'blue' },
          { skill1: 'PUG', color: 'brown' },
{ skill1: 'Vue', color: 'teal' },
{ skill1: 'PHP', color: 'indigo lighten-1' },
          { skill1: 'SQL', color: 'red' },
          { skill1: 'JavaScript', color: 'yellow' },
          { skill1: 'JQuery', color: 'indigo' },
          { skill1: 'Bootstrap', color: 'purple darken-3' },
          { skill1: 'Vuetify', color: 'blue darken-4' }
          
        ]
      },
      {
        icon: 'mdi-brush',
        title: 'UI/UX',
        img: 'figma.jpg',
        text:
          'I build responsive and functional web applications that help clients increase customer/visitor engagement.',
        skills: [{ skill1: 'Figma', color: 'blue' }]
      },
      {
        icon: 'mdi-cellphone-android',
        title: 'Mobile Application',
        img: 'flutter.png',
        text:
          "So you have an idea for a mobile app, you're in the right place. I can help you build a mobile app (Android, iOS) that meets your needs.",
        skills: [{ skill1: 'Flutter', color: 'blue accent-3' }]
      }
    ]
  }),
  inject: ['theme']
}
</script>
