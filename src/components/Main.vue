<template>
  <main>
      <div id="movie-gallery">
          <h2>movies</h2>
          <ul>
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
      <div id="series-gallery">
          <h2>series</h2>
          <ul>
              <li
              v-for="serie in series"
              :key="serie.id"
              >
                <Card 
                :italian-title="serie['name']"
                :original-title="serie['original_name']"
                :language="serie['original_language']"
                :rating="serie['vote_average']"
                />
              </li>
          </ul>
      </div>

  </main>
</template>

<script>
import Card from "./Card.vue"

export default {
    name:"Main",
    components: {
        Card,
    },
    props: ['movies','series'],
}
</script>

<style>

</style>