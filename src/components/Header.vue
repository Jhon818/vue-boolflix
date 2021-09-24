<template>
  <header class="d-flex justify-content-between">

    <span>BOOLFLIX</span>
    <input type="text" v-model="inputText" >
    <button @click="$emit('startSearch', inputText)">Search</button>
    
  </header>
</template>

<script>
export default {
  name: 'Header',

  // props: [array]

    data() {
      return {inputText: ""}
    },
    methods: {
      
    }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">


</style>
