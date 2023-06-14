<template>
  <div>

    <!-- Start All Pages -->
    <div class="all-page-title page-breadcrumb">
      <div class="container text-center">
        <div class="row">
          <div class="col-lg-12">
            <h1>Tatil Yeri Ekle</h1>
          </div>
        </div>
      </div>
    </div>
    <!-- End All Pages -->

    <!-- Start Contact -->
    <div class="contact-box">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
          </div>
        </div>
        <div class="row">
          <div class="col-lg-12">
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">

                    <input
                        type="text"
                        class="form-control"
                        id="name" name="name"
                        placeholder="Tatil Resim Url"
                        required
                        data-error="Please enter your name"
                        v-model="$v.newProduct.picture.$model"
                    >

                  </div>
                </div>
                <div class="col-md-12">
                  <div class="form-group">


                    <input
                        type="text"
                        class="form-control"
                        id="name" name="name"
                        placeholder="Yerin Adı"
                        required
                        data-error="Please enter your name"
                        v-model="$v.newProduct.name.$model"
                    >

                  </div>
                </div>
                <div class="col-md-12">
                  <div class="form-group">
                    <input
                        type="text"
                        class="form-control"
                        id="name"
                        name="name"
                        placeholder="Yerin Açıklaması"
                        required
                        data-error="Please enter your name"
                        v-model="$v.newProduct.description.$model"
                    >
                  </div>
                </div>
                <div class="col-md-12">
                  <div class="form-group">

                    <b-form-select
                        class="form-control input-border-bottom"
                        v-model="$v.selected.$model"
                        :options="listCategory()"
                    ></b-form-select>



                  </div>
                  <div class="submit-button text-center">
                    <b-button class="btn btn-common" id="submit" type="submit" @click="saveTravel" :disabled="$v.newProduct.$invalid || $v.selected.$invalid">Kaydet
                    </b-button>
                    <div id="msgSubmit" class="h3 text-center hidden"></div>
                    <div class="clearfix"></div>
                  </div>
                </div>
              </div>
          </div>
        </div>
      </div>
    </div>
    <!-- End Contact -->

  </div>
</template>

<script>
import {mapGetters} from "vuex";
import {required} from "vuelidate/lib/validators";
import Vue from "vue";

export default {
  data() {
    return {
      newProduct: {
        name: null,
        description: null,
        price: null,
        picture: null
      },
      selected: null,
      button: 'Giriş Yap',
      loginButton: false,
    }
  },
  methods: {
    saveTravel() {
      this.button = 'Yükleniyor...'
      this.loginButton = true

      let newProduct = {
        name: this.newProduct.name,
        description: this.newProduct.description,
        picture: this.newProduct.picture,
        category: this.selected
      }

      this.$store.dispatch('saveTravel', newProduct)
          .then(response => {
            if (response.status === 201){
              Vue.swal({
                text: "Onay İçin Gönderildi",
                icon: "success",
                button: false,
                timer: 2000,
                showCloseButton: false,
                showConfirmButton: false,
              });
            }else{
              Vue.swal({
                text: "Hata",
                icon: "error",
                button: false,
                timer: 3000,
                showCloseButton: false,
                showConfirmButton: false,
              });
            }
          })
    },
    listCategory() {
      const category = this.allCategory

      console.log(category)

      let categoryArray = []

      categoryArray.push({value: null, text: 'Tatil Kategorisi Seçiniz', disabled: true})

      for (let i in category) {
        categoryArray.push({value: category[i].id, text: category[i].name})
      }

      return categoryArray

    },
  },
  computed: {
    ...mapGetters(['allCategory']),
  },
  validations: {
    newProduct: {
      name: {required},
      description: {required},
      picture: {required}
    },
    selected: {required}
  }
}

</script>

<style scoped>

</style>
