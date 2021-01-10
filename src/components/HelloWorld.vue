<template>
  <!-- Product komponenta -->

  <!-- Welcome zpravicka  -->
  <div class="hello">
    <h1>{{ msg }}</h1>

    <!-- produkt  -->
    <div class="product">
      <!-- Image produktu   -->
      <div class="product-image">
        <img v-bind:src="image" />
      </div>

      <!-- Every o produktu   -->
      <div class="product-info">
        <h1>{{brand}} {{ product }}</h1>
        <p>{{ desc }}</p>
        <!-- funkce inventory   -->
         <!-- <p v-if="inventory > 10">In Stock</p>
        <p v-else-if="inventory <= 10 && inventory > 0">Almost sold out</p>
        <p v-else>Out of Stock</p>   -->

    
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
             <p>{{ sale }}</p>
   

        

        <!-- funkce sleva   -->
 

        <!-- list infa -->
        <ul>
          <li v-for="detail in details" v-bind:key="detail">{{ detail }}</li>
          <!-- velikosti-->
          <li v-for="size in sizes" v-bind:key="size">{{ size }}</li>
        </ul>
        <!-- varianty barev-->

        <div v-for="(variant,index) in variants" :key="variant.variantId"
        class="color-box" :style="{ backgroundColor:variant.variantColor}" >
        
        <!-- p @mouseover="updateProduct(variant.variantImage)">
            {{ variant.variantColor }}-->
          
          <p @mouseover="updateProduct(index)">
            {{ variant.variantColor }}
          </p>
        </div>
        <!-- <button v-on:click="cart +=1">Do košíku</button>-->

        <!-- přídat -->
        <button v-on:click="addToCart"
        :disabled="!inStock"
        :class="{disabledButton: !inStock}"
        >Přidat do košíku</button>

        <div class="cart">
          <p>Cart({{ cart }})</p>
        </div>

        <!-- Odebrat -->
        <button v-on:click="removeFromCart">Odebrat z košíku</button>

        <!-- pro click -->
        <a v-bind:href="link" target="_blank">Víc produktu</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    //DATA object
    return {
      brand:'Bitcoin',
      product: "Mikina",
      desc: "A pair of warm, fuzzy socks",
      //image:
      //  "https://hodlmoon.com/wp-content/uploads/2017/10/bitcoin-ugly-christmas-crypto-sweater.jpg",
      //vylepšeno
      selectedVariant:0,
      link: "Super produkt",
      inventory: 100,
      onSale: true,
      type: 1,
      details: ["80% bavlna", "20% polyestern", "Unisex"],
      sizes: ["S", "M", "L", "XL"],
      cart: 0,
      variants: [
        {
          variantId: 1232,
          variantColor: "red",
          variantImage:
            "https://www.fajntricko.cz/resize/e/400/400/files/mikiny--party/krypto/mikiny-bitcoin-cervena.jpg",
            variantQuantity:10
        },
        {
          variantId: 7434,
          variantColor: "black",
          variantImage:
            "https://www.fajntricko.cz/resize/e/400/400/files/mikiny--party/krypto/mikiny-bitcoin-cerna.jpg",
            variantQuantity:0
        },
        {
          variantId: 4531,
          variantColor: "grey",
          variantImage:
            "https://www.fajntricko.cz/resize/e/400/400/files/mikiny--party/krypto/mikiny-bitcoin-siva.jpg",
            variantQuantity: 55
        },
      ],
    };
  },
  methods: {
    addToCart() {
      console.log("ziju");
      this.cart += 1;
    },
    updateProduct(index) {
      this.selectedVariant = index
      console.log(index)
    },
    removeFromCart() {
      this.cart -= 1;
    },
  },

  computed:{
   
   title(){
      return this.brand +''+ this.product
    },
    image(){
      return this.variants[this.selectedVariant].variantImage
    },
    inStock(){
      return this.variants[this.selectedVariant].variantQuantity
    },
  sale(){
    if(this.onSale){
        return this.brand + ' ' + this.product + ' are on sale!'
    }
  return this.brand + ' ' + this.product + ' NOT!'
}
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin: 20px;
}

.product {
  display: flex;
}

img {
  border: 1px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  box-shadow: 0px 0.5px 1px #d8d8d8;
}

.product-image {
  flex-basis: 700px;
}

.product-info {
  margin-top: 10px;
  flex-basis: 500px;
}

button {
  margin-top: 30px;
  border: none;
  background-color: #1e95ea;
  color: white;
  height: 40px;
  width: 100px;
  font-size: 14px;
}

.cart {
  margin-right: 25px;
  background-color: pink;
  float: right;
  border: 1px solid #d8d8d8;
  padding: 5px 20px;
}

.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}


.disabledButton {
    background-color: #d8d8d8;
  }
</style>
