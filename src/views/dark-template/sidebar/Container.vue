<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Kais <span class="light-blue--text text--lighten-3">Kawar</span>
        </h1>
        <span> A challenge-loving full stack web developer </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{ item }">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{ items }">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template v-for="(item, i) in items">
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'kaiskawar@gmail.com',
            },
            {
              name: 'Website',
              icon: 'mdi-web',
              text: 'kais-viz@github.io',
            },
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: 'June 2nd, 1991',
            },
            {
              name: 'Habitation',
              icon: 'mdi-map-marker',
              text: 'Wageningen, Netherlands',
            },
          ],
        },
        socials: {
          title: 'SOCIALS',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/kais-viz',
              link: 'https://github.com/kais-viz',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/kaiskawar',
              link: 'https://linkedin.com/in/kaiskawar',
            },
            {
              icon: 'mdi-language-r',
              text: 'rpubs.com/kaisk',
              link: 'https://rpubs.com/kaisk',
            },
            {
              icon: 'mdi-alpha-k',
              text: 'kaggle.com/kaiska',
              link: 'https://www.kaggle.com/kaiska',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [
            {
              icon: 'mdi-airplane-takeoff',
              text: 'Travelling',
            },
            {
              icon: 'mdi-sheep',
              text: 'Nature',
            },
            {
              icon: 'mdi-bullseye',
              text: 'Getting out of Safe Zone',
            },
            {
              icon: 'mdi-biohazard',
              text: 'Challenges',
            },
            {
              icon: 'mdi-laptop',
              text: 'Gaming',
            },
            {
              icon: 'mdi-bike',
              text: 'Cycling',
            },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'Arabic',
              value: 100,
            },
            {
              text : 'English',
              value: 100,
            },
            {
              text : 'German',
              value: 5,
            },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar {
  background: #2e2e2e;
}
</style>
