<template>
  <main class="m-5">
      <ResultGallery id="movies" title="Film" :items="movies" it-title="title" og-title="original_title"/>
      <ResultGallery id="series" title="Serie TV" :items="series" it-title="name"  og-title="original_name"/>
  </main>
</template>

<script>
import ResultGallery from "./ResultGallery.vue";

export default {
    name:"Main",
    components: {
        ResultGallery,
    },
    props: ['movies','series'],
}
</script>

<style scoped>
</style>