<script>
import AppSearchBar from './components/AppSearchBar.vue';
import AppShowData from './components/AppShowData.vue';

export default {
  data() {
    return {
      data: [],
    }
  },
  components: {
    AppSearchBar,
    AppShowData
  },
  props:{

  },
  methods: {
    dataFromChild(pokemon){
      this.data = pokemon;
      console.log(this.data);
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
      <AppShowData />
    </div>
  </div>

</template>

<style scoped>
.app-wrap{
  height: 100%;
}
</style>
