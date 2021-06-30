<template>
  <q-layout view="lHh Lpr lFf" container style="height:100vh">
    <q-header class="bg-white">
      <q-toolbar>
        <q-btn
          flat
          dense
          color="black"
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title class="text-black">
          Matcher
        </q-toolbar-title>
        <q-btn flat no-caps @click="goCart" class="text-black">Cart ({{ totalQty }})</q-btn>
      </q-toolbar>
    </q-header>

    <q-page-container class="bg-grey-3">
      <div class="row">
        <div class="col-md-8 col-sm-12 col-lg-9">
          <ProductList />
        </div>
        <div class="col-sm-12 col-md-4 col-lg-3">
          <Cart />
        </div>
      </div>
    </q-page-container>
  </q-layout>
</template>

<script>
import { mapGetters } from 'vuex'
import Cart from '../pages/Cart.vue'
import ProductList from '../pages/ProductList.vue'
export default {
  components: {
    Cart,
    ProductList
  },
  toggleLeftDrawer: false,
  computed: {
    ...mapGetters(["cart"]),
    totalQty() {
      return this.cart.reduce((a,b) => a + b.qty, 0)
    }
  },
  methods: {
    goCart() {
      this.$router.push("/cart")
      console.log("hello");
    }
  },
}
</script>
