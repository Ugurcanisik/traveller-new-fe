<template>
  <div>
    <!-- Start All Pages -->
    <div class="all-page-title page-breadcrumb">
      <div class="container text-center">
        <div class="row">
          <div class="col-lg-12">
            <h1>Travel and Enjoy!</h1>
          </div>
        </div>
      </div>
    </div>
    <!-- End All Pages -->

    <!-- Start blog -->
    <div class="blog-box">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="heading-title text-center">
              <h2>Gezilebilecek Yerler</h2>
            </div>
          </div>
        </div>
          <div class="row">

              <div class="col-lg-4 col-md-6 col-12" v-for="travel in allTravel">
                  <div class="blog-box-inner">
                      <div class="blog-img-box" >
                          <img class="img-fluid" style="width: 570px; height: 470px;" :src="travel.picture" alt="">
                      </div>
                      <div class="blog-detail">
                          <h4>Gezilecek Yer: {{travel.name}}</h4>
                          <ul>
                              <li><span>Beğenilme: {{travel.likeCount || 0}}</span></li>
                              <li>|</li>
                              <li><span>Tarih: {{ new Date(travel.createdAt).toLocaleDateString() }}</span></li>
                          </ul>
                          <p>Açıklama: {{travel.description}}</p>

                          <router-link
                                  :to="'traveller/'+travel.id"
                          >
                              <a style="position:relative; bottom: -250px" class="btn btn-lg btn-circle btn-outline-new-white" >Detaylı Bigli</a>
                          </router-link>

                      </div>
                  </div>
              </div>

          </div>

      </div>
    </div>
    <!-- End blog -->

  </div>
</template>

<script>
import {mapGetters} from "vuex";

export default {
    computed: {
        ...mapGetters(['allCategory']),
        ...mapGetters(['allTravel'])
    }
}
</script>

<style scoped>

</style>
