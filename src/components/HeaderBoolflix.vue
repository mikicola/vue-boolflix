<template>
  <header>
    <div class="container flex">
      <h1>boolflix</h1>
      <form @submit.prevent="$emit('search', userResearch)"> <!-- @submit.prevent evita refresh pagina -->
        <input
          type="text"
          placeholder="cerca film o serie tv"
          name="search"
          v-model="userResearch"
        />
        <button>cerca</button>
      </form>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderBoolflix",
  data() {
    return {
      userResearch: '',
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: rgb(56, 56, 56);
  .container{
      justify-content: space-between;
  }
  h1 {
    text-transform: uppercase;
    color: #ff1c0b;
  }
}
</style>
