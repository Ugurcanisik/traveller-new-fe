<template>

  <div style="margin: 100px auto; width: 500px">


    <div class="modal-content">
      <div class="modal-body">


        <div class="form-group form-floating-label">
          <input
              id="picture"
              v-model="newProduct.picture"
              type="text" class="form-control input-border-bottom" required placeholder="Yerin Resim URL">
        </div>

        <div class="form-group form-floating-label" :class="{'has-error': $v.newProduct.name.$error}">
          <input
              id="productName"
              v-model="$v.newProduct.name.$model"
              type="text" class="form-control input-border-bottom" required placeholder="Yerin Adı">
        </div>

        <div class="form-group form-floating-label">
          <input
              id="prodcutDescription"
              v-model="$v.newProduct.description.$model"
              type="text" class="form-control input-border-bottom" required placeholder="Yerin Açıklaması">
        </div>

        <div class="form-group form-floating-label" :class="{'has-error': $v.selected.$error}">
          <b-form-select
              class="form-control input-border-bottom"
              v-model="$v.selected.$model"
              :options="listCategory()"
          ></b-form-select>
        </div>

      </div>
      <div class="modal-footer no-bd" style="margin: 0 auto">
        <b-button variant="primary" @click="saveTravel">Kaydet</b-button>

      </div>
    </div>

  </div>


</template>
<script>

import {required} from "vuelidate/lib/validators";
import {router} from "@/router";
import {mapGetters} from "vuex";


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
            console.log(response)
            if (response === false) {
              // this.$store.dispatch('alert', 'warning')
              // this.button = 'Giriş Yap'
              // this.loginButton = false

              // todo success
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

    }
  },
  computed: {
    ...mapGetters(['allCategory']),
  },
  validations: {
    newProduct: {
      name: {required},
      description: {required},
      price: {required},
      picture: {required}
    },
    selected: {required}
  }
}
</script>
<style scoped>
.login {
  margin-top: 25px;
  position: relative;
  left: 200px;
}

</style>
