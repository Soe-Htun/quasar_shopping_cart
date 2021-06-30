<template>
  <div class="q-pa-md ">
    <div class="q-gutter-y-md">
      <q-card class="my-card" v-for="item in cart" :key="item.id"
      flat bordered>
      <q-card-section horizontal>
        <img style="width:80px"
          :src="item.imgUrl" alt="item.title"
        />

        <q-card-actions vertical class="justify-around q-pl-lg">
          <div>{{item.title}}</div>
          <div class="row">
            <q-btn icon="add" 
              unelevated
              @click="addQty(item.id)"
              dense round size="sm"
              color="green "/>

              <div class="q-px-sm"> x {{item.qty}} </div>

              <q-btn icon="remove" 
              unelevated
              :disable="disable"
              @click="reduceQty(item.id)"
              dense round size="sm"
              color="grey-9"/>
          </div>
         
        </q-card-actions>
        <q-space />
        <q-btn 
          @click="removeItem(item.id)"
         flat icon="close" />
      </q-card-section>
    </q-card>
    </div>
    
    <q-btn v-if="cart.length" no-caps class="bg-green full-width q-mt-md" > Checkout ($ {{ totalPrice }}) </q-btn> 
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  data() {
    return {
      disable: false
    }
  },
  computed: {
    ...mapGetters(["cart"]),
    totalPrice() {
      return this.cart.reduce((a,b) => a+b.qty * b.price, 0)
    }
  },
  methods: {
    ...mapActions(["addQty","reduceQty","removeItem"]),
  },
}
</script>