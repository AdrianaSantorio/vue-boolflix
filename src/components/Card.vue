<template>
  <div class="card">
      <div class="card-text text-center d-flex flex-column align-items-center p-4 justify-content-between h-100">
        <div>
            <!-- Italian Title -->
            <h5>{{italianTitle}}</h5>
            <!-- Original title -->
            <h6 v-if="!(italianTitle === originalTitle)">{{originalTitle}}</h6>
        </div>
        <!-- Language -->
        <img 
          v-if="language === 'it' || language === 'en'" 
          :src="require(`../assets/img/${language}.png`)" 
          :alt="language" 
          class="img-fluid w-25"
        >
        <div v-else>{{language}}</div>
        <!-- overview -->
        <p>{{overview}}</p>
        <!-- star rating -->
        <div class="rating d-flex">
          <i v-for="icon in iconNumber" :key="icon" class="fa-star" :class="solidIcon(icon)  ? 'fa-solid' : 'fa-regular' "></i>
        </div>
      </div>
      <!-- Poster -->
      <img :src="poster" :alt="italianTitle" class="poster img-fluid">
  </div>
</template>

<script>
export default {
    name: "Card",
    props: ['italianTitle','originalTitle','language','rating','posterPath','overview'],
    data() {
      return {
        iconNumber: 5,
        images: {
          baseUri: 'https://image.tmdb.org/t/p/w342',
          placeholder: 'https://www.altavod.com/assets/images/poster-placeholder.png',

        }
      }
    },
    methods: {
      solidIcon(icon) {
        if ((icon) <= this.iconRating) {
          return true;
        }  else {
          return false;
        }
        
      },
    },
    computed: {
      iconRating() {
        return Math.ceil(this.rating / 2);
      },
      poster(){
        if(!this.posterPath) return this.images.placeholder;
        return this.images.baseUri + this.posterPath;
      }
    }
}
</script>

<style scoped lang="scss">
  .card {
    height: 388px;
    width: 260px;
    position: relative;
    

    .card-text {
      overflow: auto;
      background-color: #424040;
      z-index: 1;
      opacity: 0;
      transition: 1s opacity linear;
      &:hover {
        opacity: 0.8;
      }
    }

    .rating {
      color: yellow;
    }

    .poster {
      position: absolute; 
 
    }
  }

  // scrollbar
    ::-webkit-scrollbar {
          width:6px;
          padding-right: 2px;
     }

    ::-webkit-scrollbar-track {
      background: transparent;
      padding: 2px;
    }

    ::-webkit-scrollbar-thumb {
      background-color: rgba(239,220,208, 0.7);
      border-radius: 3px;
    }


</style>