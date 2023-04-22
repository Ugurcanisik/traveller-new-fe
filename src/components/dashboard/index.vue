<template>
  <div>
    <div>
      <b-carousel
          id="carousel-1"
          v-model="slide"
          :interval="4000"
          controls
          indicators
          background="#ababab"
          img-width="1024"
          img-height="480"
          style="text-shadow: 1px 1px 2px #333;"
          @sliding-start="onSlideStart"
          @sliding-end="onSlideEnd"
      >
        <!-- Text slides with image -->
        <b-carousel-slide
            v-for="trav in allTravel"
            :img-src="trav.picture"
            img-width="1024"
            img-height="480"
        ></b-carousel-slide>

      </b-carousel>

    </div>

    <!-- Start Gallery -->
    <div class="gallery-box">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="heading-title text-center">
              <h2>TRAVELLER</h2>
            </div>
          </div>
        </div>
        <div class="tz-gallery">
          <div class="row">
            <div class="col-sm-12 col-md-4 col-lg-4"  v-for="travel in allTravel">

              <router-link
                  :to="'traveller/'+travel.id"
                  tag="a"
                  class="lightbox"
              >
                <img class="img-fluid" :src="travel.picture" alt="Gallery ./images">
              </router-link>

            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- End Gallery -->



  </div>
</template>

<script>
import {mapGetters} from "vuex";

export default {
  data() {
    return {
      slide: 0,
      sliding: null
    }
  },
  computed:{
    ...mapGetters(['allTravel'])
  },
  methods: {
    onSlideStart(slide) {
      this.sliding = true
    },
    onSlideEnd(slide) {
      this.sliding = false
    }
  }
}
</script>

<style scoped>

</style>
