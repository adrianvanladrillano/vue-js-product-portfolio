<template>
  <v-app>
    <v-app-bar color="transparent" elevate-on-scroll absolute>
      <v-app-bar-nav-icon
        v-if="$vuetify.breakpoint.mobile"
      ></v-app-bar-nav-icon>
      <img
        height="50"
        contain
        src="http://kwiksurvey.co.za/wp-content/uploads/2015/03/Your-logo-here.png"
        v-if="$vuetify.breakpoint.mobile"
      />

      <v-spacer></v-spacer>

      <!-- <v-row>
        <v-col>
          <img
            height="100"
            contain
            src="http://kwiksurvey.co.za/wp-content/uploads/2015/03/Your-logo-here.png"
            v-if="!$vuetify.breakpoint.mobile"
          />
        </v-col>
      </v-row> -->

      <v-row>
        <v-col v-for="(ser, index) in series" :key="index">
          <v-menu
            offset-y
            open-on-hover
            :close-on-click="false"
            :close-on-content-click="false"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn text v-bind="attrs" v-on="on">
                {{ ser.title }}
              </v-btn>
            </template>
            <v-card style="width: 100vw">
              <v-row justify="center">
                <v-slide-group class="pa-4" active-class="success" show-arrows>
                  <v-slide-item
                    v-for="(item, index) in ser.items"
                    :key="index"
                    v-slot="{ active, toggle }"
                  >
                    <v-card
                      width="250"
                      class="mx-5 py-2 text-center"
                      flat
                      @click="$router.push('/Products/' + item.name)"
                    >
                      <v-img :src="item.image"></v-img>
                      <strong>
                        {{ item.name }}
                      </strong>
                      <br />
                      <span class="body-2">
                        {{ item.price }}
                      </span>
                    </v-card>
                  </v-slide-item>
                </v-slide-group>
              </v-row>
            </v-card>
          </v-menu>
        </v-col>
      </v-row>

      <!-- <v-btn text v-if="!$vuetify.breakpoint.mobile"> Something </v-btn>
      <v-btn text v-if="!$vuetify.breakpoint.mobile"> Something </v-btn>
      <img
        height="50"
        contain
        src="http://kwiksurvey.co.za/wp-content/uploads/2015/03/Your-logo-here.png"
        v-if="!$vuetify.breakpoint.mobile"
      />
      <v-btn text v-if="!$vuetify.breakpoint.mobile"> Something </v-btn>
      <v-btn text v-if="!$vuetify.breakpoint.mobile"> Something </v-btn> -->
      <v-spacer></v-spacer>
    </v-app-bar>
    <v-main>
      <Nuxt />
    </v-main>

    <v-footer dark padless>
      <v-card
        flat
        tile
        class="black white--text text-center py-15"
        width="100vw"
        justify="center"
      >
        <v-card align="center" color="transparent">
          <v-img
            width="200"
            src="https://cdn.logojoy.com/wp-content/uploads/2018/08/23161101/5-25.png"
          ></v-img>
        </v-card>

        <v-btn v-for="(ser, index) in series" :key="index" class="ma-5" text>
          {{ ser.title }}
        </v-btn>
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="ma-10 white--text"
            icon
          >
            <v-icon size="48px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-card-text class="white--text">
          ®{{ new Date().getFullYear() }}
          <br />
          <strong>Sample</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      icons: ['mdi-facebook', 'mdi-twitter', 'mdi-linkedin', 'mdi-instagram'],
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ]
    }
  },
  computed: {
    ...mapState({
      series: state => {
        return state.series
      }
    })
  }
}
</script>
<style>
body {
  overflow-x: hidden;
}
.v-menu__content {
  max-width: 100vw !important;
}
</style>
