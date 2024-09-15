<script>
export default {
  data() {
    return {
      msg: 'Hello!',
    }
  },
  components: {
    
  },
  props:{
    stats: Object
  },
  methods: {

  },
  mounted(){

  }
}
</script>

<template>
  <div class="d-flex align-items-center">
    <label class="col-5" for="file">{{stats.stat.name}}</label>
    <progress class="col-7 ms-2" id="file" max="255" :value="stats.base_stat"></progress>
  </div>
</template>

<style scoped>
label{
  text-transform: capitalize;
}
progress{
  color: greenyellow;
  border: greenyellow 2px solid;
  border-radius: 10px;
  background-color: #2F2F2F;
}

progress {
  --color: greenyellow; /* the progress color */
  --background: #2F2F2F; /* the background color */

  /* width: 200px; */
  /* margin: 0 10px; */
}
progress::-webkit-progress-bar {
  border-radius: 10px;
  background: var(--background);
}
progress::-webkit-progress-value {
  border-radius: 10px;
  background: var(--color);
}
</style>
