<template>
  <main class="container-lg">
      <section class="row justify-content-center">
          <Card v-for="(movie,index) in filteredList" :key="index" :card="movie"/>
      </section>
  </main>
</template>

<script>
import Card  from "./Card.vue";
export default {
    name: 'Cards',

    components: {
        Card
    },
props: {
    filteredList: Array
},



}
</script>

<style>

</style>