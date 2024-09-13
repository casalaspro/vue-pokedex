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
      <div class="info_wrap">
        <div class="card-body">
        <h5 class="card-title"> Name: <span v-if="data">{{data.name}}</span></h5>
        <h5 class="card-title"> Type:
          <span v-if="data" v-for="type in data.types"> <span v-if="data">{{ type.type.name }}</span></span>
        </h5>
        
        
        <h5 class="card-title"> Weight: <span v-if="data">{{data.weight}}</span> lb</h5>
        <h5 class="card-title"> Height: <span v-if="data">{{data.height}}</span>"</h5>
      </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>
