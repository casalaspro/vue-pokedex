<script>
import AppSearchBar from './components/AppSearchBar.vue';
import AppShowData from './components/AppShowData.vue';
import AppButtonAddRemove from './components/AppButtonAddRemove.vue';
import AppLocalList from './components/AppLocalList.vue';
import AppShowImage from './components/AppShowImage.vue';
import pokeball from './assets/pokeball.webp';


export default {
  data() {
    return {
      pokemon: undefined,
      pokemonKey: null,
      pokemonImage: pokeball,
      isPokemonWild: null,
      myPokemons: [],
      howManyReload: 1,
    }
  },
  components: {
    AppSearchBar,
    AppShowData,
    AppButtonAddRemove,
    AppLocalList,
    AppShowImage
  },
  props:{

  },
  methods: {
    copySavedPokemons(){
      if(localStorage.getItem('myPokemons') !== null){
        let lastPokeListString = localStorage.getItem('myPokemons');
        let lastPokeListObject = JSON.parse(lastPokeListString);
        this.myPokemons = lastPokeListObject;
        console.log("Pokedex starting pokemons: ", this.myPokemons);
      }else{
        console.log('No pokemon starting Pokedex.')
      }
    },
    changePokemon(pokemonName, key){
      console.log('Hai selezionato in App: ' + pokemonName + ', con chiave: ' + key);
      // i set the selected pokemon to be shown
      this.pokemon = this.myPokemons[key];
      this.pokemonImage = this.pokemon.sprites.front_default;
      // i set the pokemon key / it will be useful if we will want to delete it from the list
      this.pokemonKey = key;
      // i set if it is wild or not / it will change the button behaviour
      this.isPokemonWild = false;
      console.log('Il tuo pokemon è selvaggio? ', this.isPokemonWild);
    },
    dataFromChild(fetch){
      this.pokemon = fetch;
      this.pokemonImage = this.pokemon.sprites.front_default;
      this.isPokemonWild = true;
      console.log(this.pokemon);
    },
    ketchumAction(signal){
      if(this.isPokemonWild !== null){
        if(this.isPokemonWild){
          // i add a pokemon to the pokemon list
          this.myPokemons.push(this.pokemon);
          // i set differently the pokemon condition
          this.isPokemonWild = signal;
          // i convert json in string
          const myString = JSON.stringify(this.myPokemons);
          // i save the string inside localStorage
          localStorage.setItem('myPokemons', myString);
          console.log('La stringa salavata: ', localStorage.getItem('myPokemons'));
          // i update AppLocalList
          this.howManyReload ++;
          // console.log('La mia stringa ',myString);
        }else{
          // i change the pokemon list inside the app
          this.myPokemons.splice(this.pokemonKey, 1);
          this.pokemon = undefined;
          this.pokemonImage = pokeball;
          // i transform the object array in string
          const myPokemonsArrayString = JSON.stringify(this.myPokemons);
          // i update the data inside the localSTORAGE replacing them
          localStorage.setItem('myPokemons', myPokemonsArrayString);
          // i update AppLocalList
          this.howManyReload ++;
        }
      }
      console.log('hai cliccato da add-remove!', signal);
    }
  },
  mounted(){
    this.copySavedPokemons();
  }
}

</script>

<template>  

  <div class="app-wrap d-flex justify-content-center align-items-center">
    <div class="components">
      <div class="d-flex">
        <div class="left-side col-7">
          <AppShowImage v-bind:image="pokemonImage" />
          <AppSearchBar class="mb-3" @data-to-parent="dataFromChild"/>
          <!-- i sat the key because i reload the component each time i make +1 -->
       <!-- each time the component is reload it will update te files from localStorage -->
      <AppLocalList :key="howManyReload" @select-pokemon="changePokemon"/>
        </div>
        <div class="right-side col-5">
          <AppShowData class="mb-3" v-bind:data="pokemon"/>
          <AppButtonAddRemove class="mb-3" v-bind:isWild="isPokemonWild" @catch-or-free="ketchumAction" />
        </div>
      </div>
      
      
      
      
      <!-- <img src="./assets/pokedex_background.svg" alt=""> -->
    </div>
  </div>

</template>

<style scoped>
.components{
  background-image: url('./assets/pokedex_background.svg');
  width: 1024px;
  height: 743px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 1024px 743px;
}

.left-side{
  padding-left: 90px;
  padding-top: 222px;
}
</style>
