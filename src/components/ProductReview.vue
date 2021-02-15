<template>
   <div>
       <H1>napiš recenzi</H1>
       <form class="review-form" @submit.prevent="onSubmit">
      <p>
        <label for="name">Name:</label>
        <input id="name" v-model="name" placeholder="name">
      </p>
      
      <p>
        <label for="review">Review:</label>      
        <textarea id="review" v-model="review"></textarea>
      </p>
      
      <p>
        <label for="rating">Rating:</label>
        <select id="rating" v-model.number="rating">
          <option>5</option>
          <option>4</option>
          <option>3</option>
          <option>2</option>
          <option>1</option>
        </select>
      </p>
          
      <p>
        <input type="submit" value="Submit">  
      </p>    
    
    </form>
   </div>
</template>

<script>
 
export default {
 
  
  
  data() {
    return {
      name:null,
      review:null,
      rating:null
    }
  },
  methods: {
      onSumbit(){
          //vytvorim objekt
          let productReview={
              name:this.name,
              review:this.review,
              rating:this.rating
          }
          //resetuju
          this.$emit('review-submitted',productReview)
          this.name=null
          this.review=null
          this.rating=null
      }

  }

    
  }


  



    
</script>

<style lang="css" scoped>


textarea {
  width: 100%;
  height: 60px;
}

input {
  width: 100%;  
  height: 25px;
  margin-bottom: 20px;
}
.review-form {
  width: 20%;
  padding: 20px;
  border: 1px solid #d8d8d8;  
}

</style>