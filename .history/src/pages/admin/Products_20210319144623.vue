<template>
  <div>
    <div class="title">
      <h1>This is Admin</h1>
    </div>
    <div class="body">
      {{ product.name }}
    </div>
  </div>
</template>
<script>
export default{
    //计算属性
    computed:{
        product(){
            return this.$store.state.products[0];   

        }
    }
}
</script>
