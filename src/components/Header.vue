<template>
  <header class="d-flex justify-content-between bg-dark p-3">
    <span class="text-danger">BOOLFLIX</span>

    <div>
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
