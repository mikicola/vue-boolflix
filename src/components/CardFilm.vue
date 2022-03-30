<template>
  <div class="card">
    <h2 class="title">{{cardData.title}}</h2>
    <h3 class="original-title">{{cardData.originalTitle}}</h3>
    <small class="language">{{cardData.language}}</small>
    <small class="vote">{{cardData.vote}}</small>
  </div>
</template>

<script>
export default {
    name: 'CardFilm',
    props: {
      cardData: Object
    }
}
</script>

<style lang="scss" scoped>

</style>
