<template>


  <div id="app">
    
  <div class="nav-bar">
  </div>

     <div class="frontpage-image">
<img v-bind:src="image">
    </div>
   
    



  <HelloWorld msg="Welcome to our Store"/>
  <HelloWorld msg="Welcome to our Store"/>
  <Product :premium="premium" />
  <ProductReview @review-submitted="addReview"></ProductReview>/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Product from './components/Product.vue'
import ProductReview from './components/ProductReview.vue'







export default {
  name: 'App',
  components: {
    HelloWorld,
    Product,
    ProductReview,
    
 

    
  },
  data() {
    return {
      image: 'https://www.opennode.com/blog/wp-content/uploads/2020/04/bitcoin-button0-small.png',
      premium: true
    }
  }

}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
 
  color: #2c3e50;
 
  background-color: #bada55;
}

 body {
    font-family: tahoma;
    color:#282828;
    margin: 0px;
  }

  .nav-bar {
    background: linear-gradient(-90deg, #84CF6A, #16C0B0);
    height: 80px;
    margin-bottom: 15px;
  }
.frontpage-image{
  display: flex; 
            width: 100%;
             height:100% ;
            justify-content: center; 
}


  

  
</style>
