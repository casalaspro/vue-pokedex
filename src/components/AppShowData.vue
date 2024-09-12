<script>
export default {
  data() {
    return {
      msg: 'Hello!',
    }
  },
  props:['data'],
  components: {
    
  },
  methods: {

  },
  mounted(){

  }
}
</script>

<template>
  <div class="card-wrap mt-3">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title"> Name: {{data.name}}</h5>
        <h5 class="card-title"> Type:</h5>
        <span v-for="type in data.types">{{ type.type.name }}</span>
        
        <h5 class="card-title"> Weight: {{data.weight}} lb</h5>
        <h5 class="card-title"> Height: {{data.height}} "</h5>
        <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
