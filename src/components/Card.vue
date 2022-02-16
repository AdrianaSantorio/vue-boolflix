<template>
  <div class="card text-center d-flex flex-column align-content-center">
      <h4>{{italianTitle}}</h4>
      <h5 v-if="!italianTitle === originalTitle">{{originalTitle}}</h5>
      <img 
        v-if="language === 'it' || language === 'en'" 
        :src="require(`../assets/img/${language}.png`)" 
        :alt="language" 
        class="img-fluid w-25"
        >
      <div v-else>{{language}}</div>
      {{rating}}
      <div class="d-flex justify-content-center">
        <i v-for="star in starNumber" :key="star" class="fa-star" :class="solidStar(star)  ? 'fa-solid' : 'fa-regular' "></i>
      </div>
  </div>
</template>

<script>
export default {
    name: "Card",
    props: ['italianTitle','originalTitle','language','rating'],
    data() {
      return {
        starNumber: 5,
      }
    },
    methods: {
      solidStar(star) {
        if ((star) <= this.starRating) {
          return true;
        }  else {
          return false;
        }
        
      },
    },
    computed: {
      starRating:  function() {
        return Math.ceil(this.rating / 2);
        
      }
    }
}
</script>

<style>

</style>