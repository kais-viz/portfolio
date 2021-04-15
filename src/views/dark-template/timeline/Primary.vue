<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Experiences in Detail' : 'My Experiences'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mb-2">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2 mb-2 ml-5"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                            class="img-corners"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        detailed   : false,
        year       : '2013-2016',
        transparent: false,
        title      : 'Joined Foresite Web Design as a Frontend Web Developer',
        html       : `
                <p>
                    Built numerous Drupal client websites with tight deadlines as part of the team utilising Javascript, PHP and Python.<br>
                    Some are featured on the company <a target="_blank" href="https://foresite.jo/">website</a> till this day.
                </p>
        `,
        image      : 'img/timeline/foresite.jpg',
        imageHeight: 200,
        icon       : 'mdi-code-tags',
      },
      {
        detailed   : true,
        year       : '2017',
        transparent: true,
        title      : 'Published public domain books to Kindle Direct Publishing',
        html       : `Self-published more than 250 public domain books on Amazon’s Kindle Digital Publishing, generating over 2,500 sales. 
                      This was possible by collecting data from Goodreads API, Wikipedia API and Amazon Product API then analyzing it using advanced MongoDB queries.`,
        iconImage: 'img/timeline/kdp-logo.png',
      },
      {
        detailed   : true,
        year       : '2017-2019',
        transparent: true,
        title      : 'Worked as a full stack developer on various pojects',
        html       : `
          <ul>
          <li>MailAwesome was my brainchild business idea, a SaaS CRM helpdesk aiming to simplify customer ticketing by connecting Google Mail amongst multiple 
          users within the same organization; aimed at small-to-medium businesses.
          <ul><li>Built the backend service to automate ticket assignment amongst a team by utilising Gmail API, MongoDB and Java Spring Framework.</li></ul></li>
          <li>Self-employment meant learning to do my own project management, product development, and research projects from scratch.</li>
          <li>Built and delivered data visualization dashboards and reports, working on a contract basis with Foresite, my previous employer, 
          utilising D3/DC and native Javascript. Sample work published on github.</li>
          </ul>
        `,
        icon: 'mdi-web',
      },
      {
        year : '2019',
        title: 'Machine Learning and Data Analytics Bootcamp',
        html : `
          <p>
          Five-month full-time project-based bootcamp using realistic business cases and datasets (<a target="_blank" href="https://rpubs.com/kaisk">see RPubs</a>). 
          During the course, I built machine learning pipelines and models for multiple projects. The following are some highlights:
          </p>
          <ul>
          <li>Predicted purchasing trends using R for market basket analysis utilising historical transaction records.</li>
          <li>Analysed energy consumption patterns, reducing consumption by up to 26%.</li>
          <li>Conducted sentiment analysis for iPhone vs Samsung Galaxy. Automation of web-scraping using Common Crawl, task distribution using Amazon EMR, and analysing the text to data solutions using R.</li>
          <li>Developed an indoor positioning system by leveraging WiFi fingerprinting; reducing the error to 8m.</li>
          <li>For each project, created compelling visualisations with ggplot/plotly to present findings to the team.</li>
          </ul>
        `,
        image    : 'img/timeline/ubiqum.png',
        iconImage: 'img/timeline/ubiqum-icon.png',
      },
      {
        year       : '2020',
        detailed   : true,
        transparent: true,
        title      : 'Used Fast.ai to create neural network powered applications',
        html       : `
          <p>
            I completed part one of the <a target="_blank" href="https://course.fast.ai/">fast.ai course</a> (a Python library that sits on top of PyTorch) 
            while creating <a target="_blank" href="https://www.kaggle.com/kaiska">Kaggle kernels</a> to document my progress.
          </p>
          <p>I applied fast.ai on Kaggle competition's dataset from the 
          <a target="_blank" href="https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge">
          Facial Expression Recognition Challenge</a>. 
          It's based on lesson's <a target="_blank" href="https://course.fast.ai/videos/?lesson=1">one</a> and 
          <a target="_blank" href="https://course.fast.ai/videos/?lesson=2">two</a> of the fast.ai course. 
          <p>
          I also applied the library on an apparel image dataset that I compiled from multiple sources and creating a multi-label classification model based on what 
          I learned from Jeremy Howard's <a target="_blank" href="https://course.fast.ai/videos/?lesson=3">lesson 3</a> of the fast.ai course.
          </p>
          <p>The source codes can be found here: <a target="_blank" href="https://github.com/kais-viz/facial-recognition-fastai">kais-viz/facial-recognition-fastai</a><br>
          and here: <a target="_blank" href="https://github.com/kais-viz/multi-label-classification-fastai">kais-viz/multi-label-classification-fastai</a>
          </p>
        `,
        image      : 'img/timeline/fast-ai.png',
        imageHeight: 300,
        iconImage  : 'img/timeline/fast.ai.png',
      },
      {
        year : '2020-Present',
        title: 'Working at Omi Health Startup as a Data Scientist and Full Stack Developer',
        html : `
          <ul><li>Advanced the SIR compartmental Model formula adopted in the coronavirus predictive model.</li>
          <li>Built a dash powered website from scratch and deployed it to google’s app engine.</li>
          <li>Composed python scripts that loaded raw data from the web and sanitized it before storing it in MySQL database.</li>
          <li>Cleaned the base code and added documentation and logging to the script files.</li>
          <li>I orchestrated and developed a technology stack to move the startup to a more scalable foundation, 
          while avoiding vendor lock in. I also lead the idea to migrate the stack to AWS from Google Cloud, with a 75% reduction in costs.</li>
          <li>Fully Developed the company’s new website, the following technologies were used:</li>
          <ul><li>Vue.js and Nuxt.js frameworks for the frontend and routing of the website, increased the load speed of the graphs by more than 
          150% compared to the dash website.</li>
          <li>Strapi CMS for the backend to manage users and primarily used to serve the API endpoints.</li>
          <li>Amazon RDS (Aurora) was used as a fully managed database solution, reducing costs by eliminating the need for a database admin.</li>
          <li>Docker hub to host website images and docker swarm for easy deployment.</li>
          <li>Carefully picked graph colours to be <a target="_blank" href="https://lospec.com/palette-list/ibm-color-blind-safe">colourblind safe</a>.</li></ul></ul>
          <br>
          <p>Available on: <a target="_blank" href="http://covidplanner.nl/">covidplanner.nl</a></p>
        `,
        image    : 'img/timeline/omihealth.png',
        iconImage: 'img/timeline/covidplanner-icon.jpg',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
.img-corners {
    border-radius: 3px;
}
</style>
