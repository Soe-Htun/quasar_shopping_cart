<template>
  <q-layout view="lHh Lpr lFf" container style="height:100vh" class="rounded-borders">
    <q-header class="bg-indigo">
      <q-toolbar class="justify-between">
        <q-btn flat icon="menu" />
        <div class="text-h6">Welcome Shopping</div>
        <q-btn round flat icon="shopping_cart"/>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <q-tab-panels v-model="tab" animated>
        <q-tab-panel name="home">
          <Home />
        </q-tab-panel>
        <q-tab-panel name="cart">
          <ShoppingCart />
        </q-tab-panel>
      </q-tab-panels>
    </q-page-container>

    <q-footer class="bg-indigo">
      <q-tabs
        v-model="tab"
        dense no-caps
        align="justify"
        class="text-grey bg-indigo"
        active-color="white"
        :breakpoint="0"
      >
        <q-tab
          label="Home"
          name="home" icon="home" />
        <q-tab
          label="Cart" 
          name="cart" icon="shopping_cart" >
          <q-badge v-for="item in cart" :key="item.id"
            color="red" floating>
            {{item.qty}}
          </q-badge>
        </q-tab>
      </q-tabs>
    </q-footer>
  </q-layout>
</template>

<script>
import Home from 'src/pages/Home.vue';
import ShoppingCart from 'src/pages/ShoppingCart.vue'
import { mapGetters, mapActions } from 'vuex'
export default {
  components: {
    Home,
    ShoppingCart
  },
  data() {
    return {
      tab: "home",
    }
  },
  computed: {
    ...mapGetters(["cart"]),
  }
}
</script>
