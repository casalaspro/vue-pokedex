<script>
import AppStats from './AppStats.vue';
export default {
  data() {
    return {
      msg: 'Hello!',
    }
  },
  props:['data'],
  components: {
    AppStats
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
          <h3>INFO</h3>
          <p class="card-title"> Name: <span v-if="data">{{data.name}}</span></p>
          <p class="card-title"> Type:
            <span v-if="data" v-for="type in data.types"> <span v-if="data">{{ type.type.name }}</span></span>
          </p>
          <p class="card-title"> Weight: <span v-if="data">{{data.weight}}</span> lb</p>
          <p class="card-title"> Height: <span v-if="data">{{data.height}}</span>"</p>

          <h3>STATS</h3>
          <AppStats v-if="data" v-for="singleStat in data.stats" v-bind:stats="singleStat"/>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
span{
  text-transform: capitalize;
}

h3{
  margin: 0;
}

p{
  margin: 0;
}

.card-wrap {
    padding-top: 223px;
    /* margin-top: 300px; */
    padding-left: 16px;
}
.card{
  height: 343px;
  width: 333px;
  border: 2px solid black;
  color: greenyellow !important;
  background-color: #2F2F2F;
}
</style>
