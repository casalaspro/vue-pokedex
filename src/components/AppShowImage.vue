<script>
export default {
  data() {
    return {
      msg: 'Hello!',
    }
  },
  components: {
    
  },
  props:{
    image: String
  },
  methods: {

  },
  mounted(){
  }
}
</script>

<template>
  <div class="image-box">
    <img v-if="image !== null" :src="image" alt="">
  </div>
  
  <!-- <img src="../assets/pokedex_img.jpg" alt=""> -->
  <!-- <h2>{{ image }} prova</h2> -->
</template>

<style scoped>
  .image-box{
    width: 335px;
    height: 224px;
    border: 2px rgb(0, 0, 0) solid;
    border-radius: 10px;
    background-color: white;
    /* background-image: url('../assets/pokedex_img.jpg'); */
  }

  img{
    width: 335px;
    height: 219px;
    object-fit: contain;
  }


</style>
