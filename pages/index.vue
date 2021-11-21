<template>
  <div>
    <v-row>
      <v-col>
        <carousel />
      </v-col>
    </v-row>

    <!-- <v-row
      justify="center"
      align="center"
      style="color: black; background: #f5f5f5"
      class="py-10"
    > -->

    <v-row
      justify="center"
      align="center"
      style="color: white; background: black"
      class="py-15"
    >
      <v-col cols="10">
        <h1 class="text-center font-weight-black display-3">
          Built with quality and something.
        </h1>

        <p class="caption text-center mt-4">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Beatae unde
          eum libero, sit deleniti repellat rerum eveniet alias molestiae autem
          commodi quisquam. Aut temporibus amet quas odit similique tempora quo?
        </p>

        <v-img
          class="py-10"
          contain
          src="https://mechanicalkeyboards.com/shop/images/products/large_4322_large_DKON1861ST-USPDAZT1_main.png"
        ></v-img>
      </v-col>
    </v-row>

    <div
      v-for="(ser, index) in series"
      :key="index"
      style="padding-top: 60px; padding-bottom: 60px"
    >
      <v-container>
        <v-row
          class="text-center"
          style="padding-top: 24px; padding-bottom: 24px"
        >
          <v-col class="px-5">
            <h1 class="display-1">{{ ser.title }}</h1>
            <p class="body-2">{{ ser.subtitle }}</p>
          </v-col>
        </v-row>

        <v-row justify="center" align="center">
          <v-col
            cols="6"
            xl="2"
            v-for="(item, index) in ser.items"
            :key="index"
          >
            <v-card flat @click="$router.push('/Products/' + item.name)">
              <v-img contain :src="item.image"></v-img>

              <v-list-item two-line class="text-center">
                <v-list-item-content>
                  <v-list-item-subtitle class="subtitle-1 text-wrap">
                    {{ item.name }}
                  </v-list-item-subtitle>
                  <v-list-item-title class="font-weight-bold title">
                    ₱{{ item.price }}
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </div>

    <v-row
      justify="center"
      align="center"
      style="height: 100vh; background: #f0f2f5"
    >
      <v-col cols="10">
        <h1 class="display-3 text-center font-weight-medium">
          Gaming never ends.
        </h1>
        <p class="body-2 text-center mt-2 text--secondary">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis ad
          cupiditate earum soluta eligendi.
        </p>
        <v-img
          contain
          src="https://mechanicalkeyboards.com/shop/images/products/large_4322_large_DKON1861ST-USPDAZT1_main.png"
        ></v-img>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import { mapState } from 'vuex'
export default {
  data() {
    return {}
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