<template>
  <div id="id" class="container">
          <h2>{{title}}</h2>
          <div class="row g-4">
            <div 
            class="col-6 col-md-4 col-lg-3"
            v-for="item in items" 
           :key="item.id" 
           :item="item"
            >
                <Card 
                :italian-title="item[itTitle]"
                :original-title="item[ogTitle]"
                :language="item['original_language']"
                :rating="item['vote_average']"
                :poster-path="item['poster_path']"
                :overview="item['overview']"
            />
            </div>
          </div>
      </div>
</template>

<script>
import Card from "./Card.vue"

export default {
    name: "ResultGallery",
    components:{Card},
    props: ["id", "title", "items","itTitle","ogTitle"],

}
</script>

<style scoped>


</style>