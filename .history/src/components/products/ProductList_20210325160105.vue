<template>
  <div>
    <div class="products">
      <div class="container">
        This is ProductList
      </div>
      <template v-for="product in products">
        <product-item :product="product" :key="product._id"></product-item>
      </template>
    </div>
  </div>
</template>

<style>
.product {
  border-bottom: 1px solid black;
}

.product__image {
  width: 100px;
  height: 100px;
}
</style>

<script>

import ProductItem from './ProductItem.vue';
export default {
  name: 'product-list',
  created(){
      if(this.products.length === 0){
          //判断是否本地有数据没有就axios取值
          this.$store.dispatch('allProducts');
      }
  },
  computed: {
    // a computed getter
    products() {
      return this.$store.state.products;
    }
  },
  methods: {
    addToCart(product) {
      this.$store.commit('ADD_TO_CART', {
        product
      });
    }
  },
  components: { 
    'product-item':ProductItem 
    }
}
</script>
