<template>
   <div class="flip-card col-sm-3 col-md-2 col-xl-3 m-3 p-0 ">
  <div class="flip-card-inner">
    <div class="flip-card-front">
     <img
      class="h-100 w-100 image-fluid"
      :src="'https://image.tmdb.org/t/p/original/' + card.poster_path"
      alt="'image not found'"
    />
    </div>
    <div class="flip-card-back">
     <div>
      <i v-for="n in 5" :key="n" class="fa-star" :class="n <= getVote() ? 'fas' : 'far' "></i>
    </div>

    <div class=" d-flex flex-column">
       <span>TITLE:{{ card.title }}</span>
      <span>overview: <br>
       {{ card.overview }}</span>
    </div>
     <span v-if="card.original_language == 'fr'">Language:<svg class="flag" version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="-10 -10 3020 2020"><g id="French_Flag_by_Adam_Stanislav"><title>Flag of France, by Adam Stanislav</title><rect fill="rgb(0%,14%,58%)" x="0" y="0" width="1010" height="2000" /><rect fill="rgb(97%,97%,97%)" x="1000" y="0" width="1010" height="2000" /><rect fill="rgb(93%,16%,22%)" x="2000" y="0" width="1000" height="2000" /><rect fill="none" stroke="rgb(55%,55%,55%)" stroke-width="10" x="0" y="0" width="3000" height="2000" /></g></svg></span>
      <span v-if="card.original_language == 'en'">Language:<svg class="flag" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 60 30" ><clipPath id="s"><path d="M0,0 v30 h60 v-30 z"/></clipPath><clipPath id="t"><path d="M30,15 h30 v15 z v15 h-30 z h-30 v-15 z v-15 h30 z"/></clipPath><g clip-path="url(#s)"><path d="M0,0 v30 h60 v-30 z" fill="#012169"/><path d="M0,0 L60,30 M60,0 L0,30" stroke="#fff" stroke-width="6"/><path d="M0,0 L60,30 M60,0 L0,30" clip-path="url(#t)" stroke="#C8102E" stroke-width="4"/><path d="M30,0 v30 M0,15 h60" stroke="#fff" stroke-width="10"/><path d="M30,0 v30 M0,15 h60" stroke="#C8102E" stroke-width="6"/></g></svg></span>
      <span v-if="card.original_language == 'pl'">Language:<svg class="flag" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 10"><path fill="#fff" d="M0 0h16v10H0z"/><path fill="#dc143c" d="M0 5h16v5H0z"/></svg></span>
    </div>
  </div>
</div> 
</template>

<script>

export default {
  props: {
    card: Object,
  },

  methods: {
    getVote() {
      return Math.ceil(this.card.vote_average / 2)
    }
  }
};
</script>


<style lang="scss">
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 500px;
  border: 1px solid #f1f1f1;
  perspective: 1000px;
 
  

  .flag {
   width: 50px;
 }

 
.flip-card-inner {
 position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}
  }


.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}


.flip-card-front, .flip-card-back {
  position: absolute;
  height: 100%;
  overflow-y: hidden;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;
  width: 100%;
  height: 100%;
}


.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
   position: inherit;
}


</style>