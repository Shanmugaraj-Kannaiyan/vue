<template>
  <div class="container">
    <h1 class="head">Inforios </h1>
    <button class="products" @click="products" >products </button>
     </div>
</template>

<script>
export default {
data(){
    return {

    }
    
},
method:{
  products(){
    this.$axios.$get('http://192.168.1.27:2000/product')
    .then(res=>{
      console.log('product data', res);
    }).catch(err =>{
      console.log('product error',err);
    })
  }
}
}
</script>

<style>

</style>