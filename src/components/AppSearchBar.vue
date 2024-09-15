<script>
import axios from 'axios'

export default {
  data() {
    return {
      msg: 'Hello!',
      searchbar: '',
      fetch: [],
    }
  },
  emits:[
    'data-to-parent'
  ],
  components: {
    
  },
  props:{

  },
  methods: {
    fetchPokemon(){
      axios({
        method: 'get',
        url: 'https://pokeapi.co/api/v2/pokemon/' + this.searchbar,
      })
      .then((response)=>{
        this.fetch = response.data;
        console.log(this.fetch);
        this.dataToParent();
      })
      .catch((error)=>{
        console.log(error.response.data);
      });
    },
    dataToParent(){
      this.$emit('data-to-parent', this.fetch);
      console.log('vada data');
    }
  },
  mounted(){

  }
}
</script>

<template>
  <!-- <h1>{{ msg }}</h1> -->
  <div class="searchBarWrap">
    <input placeholder="..search your pokemon" class="me-3" v-model="searchbar" type="text">
    <button @click="fetchPokemon" class="btn btn-danger button-search" type="submit">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path fill="black" d="M416 208c0 45.9-14.9 88.3-40 122.7L502.6 457.4c12.5 12.5 12.5 32.8 0 45.3s-32.8 12.5-45.3 0L330.7 376c-34.4 25.2-76.8 40-122.7 40C93.1 416 0 322.9 0 208S93.1 0 208 0S416 93.1 416 208zM208 352a144 144 0 1 0 0-288 144 144 0 1 0 0 288z"/></svg>
    </button>
  </div>
  
  <!-- <h2>{{ searchbar }}</h2> -->
</template>

<style scoped>
button > svg{
  width: 20px;
}

.searchBarWrap{
  padding-left: 20px;
}

input{
  border-radius: 4px;
  border: 2px solid black;
}

.button-search{
  padding: 14px 20px;
  margin-top: 8px;
  border: 2px solid black;
  background-color: #E1E061;
}
</style>
