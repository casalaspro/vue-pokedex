<script>
import AppSearchBar from './components/AppSearchBar.vue';
import AppShowData from './components/AppShowData.vue';

export default {
  data() {
    return {
      pokemon: undefined,
      test: {
        pino: 'landi'
      }
    }
  },
  components: {
    AppSearchBar,
    AppShowData
  },
  props:{

  },
  methods: {
    dataFromChild(fetch){
      this.pokemon = fetch;
      console.log(this.pokemon);
    }
  },
  mounted(){

  }
}

</script>

<template>  

  <div class="app-wrap d-flex justify-content-center align-items-center">
    <div class="components">
      <AppSearchBar @data-to-parent="dataFromChild"/>
      <AppShowData v-bind:data="pokemon"/>
    <!-- <h1>Prova: {{ test.pino }}</h1> -->
    </div>
  </div>

</template>

<style scoped>

</style>
