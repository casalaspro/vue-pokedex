<script>
import AppSearchBar from './components/AppSearchBar.vue';
import AppShowData from './components/AppShowData.vue';
import AppButtonAddRemove from './components/AppButtonAddRemove.vue';
import AppLocalList from './components/AppLocalList.vue';


export default {
  data() {
    return {
      pokemon: undefined,
      isPokemonWild: null,
      test: {
        pino: 'landi'
      },
      myPokemons: [],
      howManyReload: 1,
    }
  },
  components: {
    AppSearchBar,
    AppShowData,
    AppButtonAddRemove,
    AppLocalList
  },
  props:{

  },
  methods: {
    dataFromChild(fetch){
      this.pokemon = fetch;
      this.isPokemonWild = true;
      console.log(this.pokemon);
    },
    ketchumAction(signal){
      if(this.isPokemonWild ==! null){
        if(this.isPokemonWild){
          // i add a pokemon to the pokemon list
          this.myPokemons.push(this.pokemon);
          // i set differently the cpokemon condition
          this.isPokemonWild = signal;
          // myPokemons works
          // console.log(this.myPokemons);
          // i convert json in string
          const myString = JSON.stringify(this.myPokemons);
          // i save the string inside localStorage
          localStorage.setItem('myPokemons', myString);
          console.log('La stringa salavata: ', localStorage.getItem('myPokemons'));
          this.howManyReload ++;
          // console.log('La mia stringa ',myString);
        }
      }
      console.log('hai cliccato da add-remove!', signal);
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
      <AppButtonAddRemove v-bind:isWild="isPokemonWild" @catch-or-free="ketchumAction" />
      <!-- i sat the key because i reload the component each time i make +1 -->
       <!-- each time the component is reload it will update te files from localStorage -->
      <AppLocalList :key="howManyReload" />
    </div>
  </div>

</template>

<style scoped>

</style>
