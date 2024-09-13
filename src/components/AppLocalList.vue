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
  methods: {
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
  <h1>My Pokemons</h1>

  <div class="card">
    <div class="card-body">
      <table class="table table-striped">
        <tr v-for="pokemon in myList">
          <td>{{ pokemon.name }}</td>
        </tr>
      </table>
      <!-- <div class="my-list">
        <h1 v-for="pokemon in myList" >{{ pokemon.name }}</h1>
      </div> -->
    </div>
  </div>
</template>

<style scoped>

</style>
