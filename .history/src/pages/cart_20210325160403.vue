<template>
  <div>
    <div class="title">
      <h1>{{msg}}</h1>
    </div>
    <template v-for="product in cart">
      <product-item  :product="product" :key="product._id"> </product-item>
    </template>
  </div>
</template>
<style>
.product{
  border-bottom: 1px solid black;
}
.product__image{
  width: 100px;
  height: 100px;
}

</style>
<script>
import ProductItem from '@/components/products/ProductItem.vue';
export default {
    name:'home',
    data(){
        return{
            msg:'welcome to the cart page'
        }
    },
    computed:{
        cart() {
            return this.$store.state.cart;
        }
    },
    methods:{
        removeFromCart(productId){
            this.$store.commit('REMOVE_FROM_CART',{
                productId
            });
        }
    },
    components:{
      'product-item':ProductItem
    }
}
</script>