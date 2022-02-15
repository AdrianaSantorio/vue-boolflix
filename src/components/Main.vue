<template>
  <main>
      <div id="movie-gallery">
          <ul 
           
           >
              <li
                v-for="movie in movies" 
               :key="movie.id"
                >
                <Card 
                :italian-title="movie['title']"
                :original-title="movie['original_title']"
                :language="movie['original_language']"
                :rating="movie['vote_average']"
                />
              </li>
          </ul>
      </div>
      <div id="series-gallery"></div>

  </main>
</template>

<script>
import Card from "./Card.vue"

export default {
    name:"Main",
    components: {
        Card,
    },
    props: ['movies'],
}
</script>

<style>

</style>