<template>
  <div>
    <v-row
      justify="center"
      align="center"
      class="py-15"
      v-if="series.length != 0"
    >
      <v-col cols="12" xl="5" class="px-10 text-center">
        <v-img class="py-10" contain :src="product_image"></v-img>

        <h1 class="text-center font-weight-black display-3">
          {{ product_name }}
        </h1>

        <p>
          {{ loadProduct }}
        </p>

        <p class="caption text-center mt-5">
          Color name : Bloody Red Eyes : Clear (Shine through) Material: Resin
          Switch type: Cherry mx Handmade Only for mechanical keyboard Hot Keys
          Project
        </p>

        <v-btn class="mr-2" color="black" dark> Buy on lazada </v-btn>
        <v-btn> Buy on shopee </v-btn>
      </v-col>
    </v-row>

    <v-row dense>
      <v-col v-for="gal in product_gallery" :key="gal">
        <v-card>
          <v-img
            width="100%"
            height="100%"
            :src="gal"
            @click="showImage(gal)"
          ></v-img>
        </v-card>
      </v-col>
    </v-row>

    <v-dialog v-model="dialogImage" width="800">
      <v-card>
        <v-img :src="dialogUrl"></v-img>
      </v-card>
    </v-dialog>

    <!-- <v-row
      justify="center"
      align="center"
      class="mb-15"
      style="background: #e1e1e1"
    >
      <v-col>
        <v-slide-group
          v-model="model"
          class="pa-4"
          active-class="success"
          show-arrows
        >
          <v-slide-item
            v-for="gal in product_gallery"
            :key="gal"
            v-slot="{ active, toggle }"
          >
            <v-col xl="4">
              <v-img width="100%" height="100%" :src="gal"></v-img>
            </v-col>
          </v-slide-item>
        </v-slide-group>
      </v-col>
      <v-col cols="8" fill-height>
        <v-row>
          <v-col cols="4" v-for="gal in product_gallery" :key="gal">
            <v-img height="100%" :src="gal"></v-img>
          </v-col>
        </v-row>
      </v-col>
    </v-row> -->
  </div>
</template>
<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      product_name: '',
      product_image: '',
      dialogUrl: false,
      dialogImage: ''
    }
  },
  computed: {
    ...mapState({
      series: state => {
        return state.series
      }
    }),
    loadProduct() {
      this.series.forEach(element => {
        let index = element.items
          .map(el => el.name)
          .indexOf(this.$route.params.id)
        console.log(index)
        if (index != -1) {
          this.product_name = element.items[index].name
          this.product_image = element.items[index].image
          this.product_gallery = element.items[index].gallery
        }
      })
    }
  },
  methods: {
    showImage(url) {
      this.dialogUrl = url
      this.dialogImage = true
    }
  }
}
</script>