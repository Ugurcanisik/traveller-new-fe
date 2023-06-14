<template>
  <!-- Start header -->
  <header class="top-navbar">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container">
        <a class="navbar-brand" href="index.html">
          <img src="images/logo.png" alt=""/>
        </a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbars-rs-food"
                aria-controls="navbars-rs-food" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbars-rs-food">
          <ul class="navbar-nav ml-auto">


            <router-link
                active-class="active"
                to="/dashboard"
                tag="li"
                class="nav-item">
              <a class="nav-link">
                <p>Anasayfa</p>
              </a>
            </router-link>

            <router-link
                active-class="active"
                to="/traveller"
                tag="li"
                class="nav-item">
              <a class="nav-link">
                <p>Yolculuklar</p>
              </a>
            </router-link>


            <router-link
                active-class="active"
                to="/about"
                tag="li"
                class="nav-item">
              <a class="nav-link">
                <p>Hakkımızda</p>
              </a>
            </router-link>


            <router-link
                active-class="active"
                to="/community"
                tag="li"
                class="nav-item">
              <a class="nav-link">
                <p>Çok Beğenildi</p>
              </a>
            </router-link>

            <router-link
                active-class="active"
                to="/contact"
                tag="li"
                class="nav-item">
              <a class="nav-link">
                <p>İleşitim</p>
              </a>
            </router-link>


            <li
                class="nav-item dropdown"
                v-if="!getUser"
            >
              <a class="nav-link dropdown-toggle" href="#" data-toggle="dropdown">Giriş Yap/Üye Ol</a>
              <div class="dropdown-menu" aria-labelledby="dropdown-a">

                <router-link
                    style="width: 140px;height: 50px; text-align: center"
                    to="/login"
                    tag="a"
                    class="dropdown-item"
                >
                  <p>Giriş Yap</p>
                </router-link>

                <router-link
                    style="width: 140px;height: 50px; text-align: center"
                    to="/signup"
                    tag="a"
                    class="dropdown-item"
                >
                  <p>Üye Ol</p>
                </router-link>

              </div>
            </li>

            <li
                v-else
                class="nav-item dropdown"
            >
              <a class="nav-link dropdown-toggle" href="#"
                 data-toggle="dropdown">{{ getUser.firstName + " " + getUser.lastName }}</a>
              <div class="dropdown-menu" aria-labelledby="dropdown-a">
                <router-link
                    to="/add-travel"
                    tag="a"
                    class="dropdown-item"
                >
                  Tatil Yeri Ekle
                </router-link>

                <a class="dropdown-item" @click="logout">Logout</a>
              </div>
            </li>


          </ul>
        </div>
      </div>
    </nav>
  </header>
  <!-- End header -->
</template>

<script>
import {mapGetters} from "vuex";

export default {
  data() {
    return {
      checkUser: false
    }
  },
  computed: {
    ...mapGetters(['getUser']),
    ...mapGetters(['isAuthenticated'])
  },
  watch: {},
  methods: {
    logout() {
      this.$store.dispatch('logout')
    },
    addTravel() {
      this.$store.dispatch('logout')
    }
  }
}
</script>

<style scoped>

</style>
