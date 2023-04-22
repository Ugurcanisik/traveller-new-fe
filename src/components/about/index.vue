<template>
  <div>
    <!-- Start About -->
    <div class="about-section-box" >
      <div class="container" style="margin-top: 420px">
        <div class="row">
          <div class="col-lg-6 col-md-6 text-center">
            <div class="inner-column">
              <h1>Tatil Öner'e Hoşgeldiniz</h1>
              <h4>Hikayemiz</h4>
              <p> Buradaki amacımız bizi takip eden takipçilerimizin gezdikleri güzel yerleri başkaları da gezsin diye bizimle paylaşması sonucu sizler ile bu güzel gezilecek yerli bir araya getiriyoruz!</p>
                <router-link
                        :to="'traveller'"
                >
                    <a class="btn btn-lg btn-circle btn-outline-new-white" href="#">Hadi Gezilecek Yerler Bakalım!</a>
                </router-link>
            </div>
          </div>

        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {}
</script>

<style scoped>

</style>
