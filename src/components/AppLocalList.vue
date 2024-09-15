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
    <div class="card">
      <div class="card-body">
        <h3 class="">My Pokemons</h3>
        <div class="line"></div>
        <table class="table mt-1 table-striped">
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
  color: greenyellow;
}

.line{
  color: greenyellow;
  border: 1px solid greenyellow;
}

.my-pokemon-wrap{
    margin-top: 30px;
    margin-left: 2px;
    width: 222px;
    height: 155px;
    overflow-y: scroll;
    border-radius: 12px;
    border: solid black 2px;
    color: greenyellow !important;
    background-color: #2F2F2F;
}

td:hover{
    background-color: greenyellow;
    color: #2F2F2F;
    /* color: white; */
    border-radius: 4px;
  }
.card-body{
  background-color: #2F2F2F
}

.card{
  background-color: #2F2F2F
}
h3{
  color: greenyellow;
  text-transform: uppercase;
}
</style>
