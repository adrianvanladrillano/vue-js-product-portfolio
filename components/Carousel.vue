<template>
  <v-carousel
    cycle
    height="100vh"
    hide-delimiter-background
    show-arrows-on-hover
  >
    <v-carousel-item v-for="(slide, i) in slides" :key="i">
      <v-sheet :color="colors[i]" height="100%" style="background: #eeeeee">
        <v-row class="fill-height" align="center" justify="center">
          <v-col></v-col>
          <v-col cols="12" xl="4">
            <v-card flat color="transparent" width="500" class="px-5">
              <v-card-title class="display-2 font-weight-black">
                Hannya Series
              </v-card-title>
              <v-card-text>
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
                Adipisci, sunt. Fuga animi, maxime quos ipsam nesciunt iure
                reiciendis debitis quae impedit non doloribus laborum assumenda
                dolore possimus harum dicta quidem.
              </v-card-text>

              <v-img src="/2.png"></v-img>

              <v-card-actions class="mt-5">
                <v-btn class="px-10" depressed color="black" dark elevation="15"
                  >Get Started</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-col>
          <v-col cols="12" xl="6">
            <v-img contain src="/test.png"></v-img>
          </v-col>
        </v-row>
      </v-sheet>
    </v-carousel-item>
  </v-carousel>
</template>
<script>
export default {
  data() {
    return {
      colors: ['white', 'white', 'white', 'grey lighten-4', 'white'],
      slides: ['First', 'Second', 'Third', 'Fourth', 'Fifth']
    }
  }
}
</script>