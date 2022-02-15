<template>
  <div class="card">
      <h4>{{italianTitle}}</h4>
      <h5 v-if="!italianTitle === originalTitle">{{originalTitle}}</h5>
      <div>{{language}}</div>
      <!-- <img :src="require(`../assets/img/${language}.png`)" :alt="language"> -->
      {{rating}}
      <i v-for="(star, index) in 5" :key="index" class="fa-star" :class=" solidStar(index)  ? 'fa-solid' : 'fa-regular' "></i>
  </div>
</template>

<script>
export default {
    name: "Card",
    props: ['italianTitle','originalTitle','language','rating'],
    data() {
      return {
      }
    },
    methods: {
      solidStar(index) {
        if ((index + 1) <= this.starRating) {
          return true;
        }  else {
          return false;
        }
        
      },
    },
    computed: {
      starRating:  function() {
        return Math.floor(parseInt(this.rating / 2));
        
      }
    }
}
</script>

<style>

</style>