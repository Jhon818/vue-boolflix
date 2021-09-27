<template>
  <div
    class="
      position-relative
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
    <div class="position-absolute h-100 w-100 description">
      <span>TITLE:{{ card.title }}</span>
      <span>TITLE2:{{ card.original_title }}</span>
      <span>VOTES: {{ card.vote_average }}</span>
      <span>VOTES: {{ card.overview }}</span>

      <span v-if="card.original_language == 'en'">Language: &#127468;</span>
      <span v-if="card.original_language == 'fr'">Language: &#127467;</span>
      <span v-if="card.original_language == 'pl'">Language: &#127477;</span>
    </div>

    <!-- languages -->

    <img
      class="h-100 w-100 position-absolute"
      :src="'https://image.tmdb.org/t/p/original/' + card.poster_path"
      alt="'image not found'"
    />
  </div>
</template>

<script>
export default {
  props: {
    card: Object,
  },
};
</script>


<style lang="scss">
div.cards {
  display: flex;
  height: 20rem;
  overflow-y: auto;
}
 div.cards:active {
   img {
      display: none;
   }
  .description {
    display: contents;
  }
 }


</style>