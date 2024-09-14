<script>
export default {
  data() {
    return {
      myList: null,
    }
  },
  components: {
    
  },
  props:{

  },
  emits:[
    'select-pokemon'
  ],
  methods: {
    selectPokemon(pokemonName, key){
      console.log('You selected: ' + pokemonName + ', with key: ' + key);
      this.$emit('select-pokemon', pokemonName, key);
    },
    checkPokemons(){
      if(localStorage.getItem('myPokemons') !== null){
        let updatedListString = localStorage.getItem('myPokemons');
        let updatedListObject = JSON.parse(updatedListString);
        this.myList = updatedListObject;
        console.log('la mia lista', this.myList)
      }else{
        console.log('control went wrong');
      }
      // console.log('controllo dalla lista', localStorage.getItem('myPokemons') !== null);
      
    }
  },
  mounted(){
    this.checkPokemons();
  }
}
</script>

<template>
  <div class="my-pokemon-wrap mb-3">
    <h1 class="mb-3">My Pokemons</h1>
    <div class="card">
      <div class="card-body">
        <table class="table table-striped">
          <tr v-for="(pokemon, key) in myList">
            <td @click="selectPokemon(pokemon.name, key)" class="px-2">{{ pokemon.name }}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<style scoped>
td{
  text-transform: capitalize;
}

td:hover{
    background-color: #DC3546;
    color: white;
    border-radius: 4px;
  }
</style>
