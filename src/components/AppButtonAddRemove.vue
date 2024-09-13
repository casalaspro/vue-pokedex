<script>
export default {
  data() {
    return {
      wild: null,
    }
  },
  components: {
    
  },
  props:{
    isWild : Boolean
  },
  emits:[
    'catch-or-free'
  ],
  methods: {
    catchOrFree(isWild){
      this.wild = isWild;
      this.$emit('catch-or-free', this.wild);
      // console.log('hai cliccato dentro');
      // console.log('isWild?', isWild);
    }
  },
  mounted(){

  }
}
</script>

<template>
  <button @click="catchOrFree(isWild)" class="btn btn-danger" type="submit"><span v-if="wild === true || wild === null">Catch It!</span ><span v-else>Set It free!</span></button>
</template>

<style scoped>

</style>
