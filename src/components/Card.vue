<template>
  <div
    class="
      cards
      bg-dark
      text-light
      col-3
      m-3
      justify-content-center
      align-items-center
      flex-column
    "
  >
    <img :src="card.backdrop_path" alt="" />
    <span>TITLE:{{ card.title }}</span>
    <span>TITLE2:{{ card.original_title }}</span>
    <span>LANGUAGE:{{ $languege }}</span>
    <span>VOTES: {{ card.vote_average }}</span>
  </div>
</template>

<script>
export default {
  props: {
    card: Object,
  },

  mounted () {
  console.log('updated: ', this.card.poster_path +  'text')
},
};


</script>


<style lang="scss">
div.cards {
  display: flex;
  height: 20rem;
  overflow-y: auto;
}

//  @if $languege {
    
//  }


</style>