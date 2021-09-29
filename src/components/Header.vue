<template>
  <header class="d-flex justify-content-between bg-dark p-3">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand text-danger" href="#">BOOLFLIX</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a class="nav-link active" aria-current="page" href="#">Home</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Serie Tv</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Film</a>
        </li>
        <li class="nav-item">
          <a class="nav-link ">Originali</a>
        </li>
      </ul>
    </div>
  </div>
</nav>

    <div class="d-flex align-items-center">
      <input type="text" v-model="inputText" />
      <button @click="$emit('startSearch', inputText)">Search</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return { inputText: "" };
  },
  methods: {},
};
</script>

<style scoped lang="scss">
</style>
