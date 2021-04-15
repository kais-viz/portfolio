<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section title="Who am I?">
        I am a Full Stack Developer and Data Scientist born in Jordan.<br>
        I am skilled in different topics of Computer Science including frontend &amp; backend development, data analytics. and machine learning.
      </content-section>
      <!-- <content-section
        v-if="prouds"
        title="What am I proud of?"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section> -->
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template v-for="(skill, i) in skills">
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div class="mr-2 ml-2">
                <div class="align-center">
                  <v-icon small>
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    educations: [
      {
        from       : '2019',
        to         : '2019',
        title      : "Bachelor's degree, Information Technology",
        location   : 'Ubiqum Code Academy',
        description:
          'Five-month full-time project-based bootcamp using realistic business cases and datasets (see RPubs). During the course, I built machine learning pipelines and models for multiple projects.',
      },
      {
        from       : '2012',
        to         : '2013',
        title      : "Master's degree, Computer Science",
        location   : 'University of Liverpool',
        description:
          'Thesis: Developed and designed an iOS recipe app, built with Objective C and CodeIgniter.',
      },
      {
        from       : '2009',
        to         : '2012',
        title      : "Bachelor's degree, Civil Engineering",
        location   : 'University of Liverpool',
        description:
          'Thesis: Modelled residual pollution from the Mersey Estuary and impact on the estuary.',
      },
    ],
    skills: [
      {
        title: 'JavaScript',
        icon : 'mdi-language-javascript',
        value: 85,
      },
      {
        title: 'Vue.js',
        icon : 'mdi-vuejs',
        value: 75,
      },
      {
        title: 'Nuxt.js',
        icon : 'mdi-vuejs',
        value: 75,
      },
      {
        title: 'Python',
        icon : 'mdi-language-python',
        value: 90,
      },
      {
        title: 'R Language',
        icon : 'mdi-language-r',
        value: 75,
      },
      {
        title: 'Docker',
        icon : 'mdi-docker',
        value: 65,
      },
      { divider: true },
      {
        title: 'MySQL',
        icon : 'mdi-database',
        value: 65,
      },
      {
        title: 'Git',
        icon : 'mdi-git',
        value: 88,
      },
      {
        title: 'Tailwind CSS',
        icon : 'mdi-sass',
        value: 90,
      },
      {
        title: 'Amazon Web Services',
        icon : 'mdi-aws',
        value: 45,
      },
      {
        title: 'Dash',
        icon : 'mdi-language-python',
        value: 90,
      },
      {
        title: 'Fast Ai',
        icon : 'mdi-code-tags',
        value: 55,
      },
      {
        title: 'SASS',
        icon : 'mdi-sass',
        value: 55,
      },
      {
        title: 'Tableau',
        icon : 'mdi-periodic-table',
        value: 49,
      },
      { divider: true },
      {
        title: 'Responsive Web Design',
        icon : 'mdi-web',
        value: 90,
      },
      {
        title: 'Machine Learning',
        icon : 'mdi-robot-vacuum',
        value: 50,
      },
      {
        title: 'Data Visualization',
        icon : 'mdi-chart-areaspline',
        value: 75,
      },
      {
        title: 'Data Analytics',
        icon : 'mdi-google-analytics',
        value: 80,
      },
      {
        title: 'Google Adwords',
        icon : 'mdi-google-adwords',
        value: 40,
      },
      {
        title: 'Search Engine Optimization',
        icon : 'mdi-chart-line',
        value: 69,
      },
      {
        title: 'Continuous Integration / Continuous Delivery',
        icon : 'mdi-truck-fast',
        value: 5,
      },
      { divider: true },
      {
        title: 'Teamwork',
        icon : 'mdi-account-group',
        value: 68,
      },
      {
        title: 'Problem Solving',
        icon : 'mdi-lightbulb',
        value: 86,
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
