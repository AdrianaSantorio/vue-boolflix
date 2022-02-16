<template>
  <main>
      <ResultGallery id="movies" title="Film" :items="movies" it-title="title" og-title="original-title"/>
      <ResultGallery id="series" title="Serie TV" :items="series" it-title="name"  og-title="original-name"/>
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

<style>

</style>