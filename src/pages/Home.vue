<template>
    <div class="q-pa-md">
    <div class="row q-col-gutter-md">
      <div class="col-6 col-md-4 col-sm-12" v-for="item in products" :key="item.id">
        <q-card class="my-card">
         <img :src="item.imgUrl" alt="item.imgUrl" />
          <q-card-section>
            <div class="text-subtitle1 text-capitalize text-center ellipsis"> {{item.title}}</div>
            <div class="text-subtitle1 text-bold text-center"> $ {{item.price}}</div>
            <div class="column items-center">

            <q-btn label="Add to cart" color="indigo"
              @click="addToCart(item)" 
              no-caps unelevated
              class="q-px-md q-mt-sm"
            />
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
export default {
  data() {
    return {
      
    }
  },
  computed: {
    ...mapGetters(["products"])
  },
  methods: {
    ...mapActions(["getProducts", "addToCart"])
  },
  created() {
    this.getProducts();
  },
}
</script>