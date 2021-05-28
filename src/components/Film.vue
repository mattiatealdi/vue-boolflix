<template>
<div class="films">
  <div class="film">
      <ul>
          <li v-if="film.name == undefined">Titolo: {{ film.title }} </li> <li v-if="film.title == undefined ">Titolo: {{ film.name }}</li>
          <li v-if="film.original_name == undefined">Titolo originale: {{ film.original_title}}</li><li v-if="film.original_title == undefined "> Titolo originale: {{ film.original_name }}</li>
          <li v-if="film.original_language == 'it'">Lingua: {{ film.original_language }} <country-flag country='it' size='small'/></li>
          <li v-if="film.original_language =='en'">Lingua: {{film.original_language}} <country-flag country='gb' size='small'/> </li>
          <li class="voto">Voto: <i v-for="(circle,index) in numCircles(film.vote_average)" :key="index" class="fas fa-star"></i></li>
          <li>Overview: {{ film.overview }}</li>
      </ul>
  </div>
  <div class="film_img">
      <img :src=" 'https://image.tmdb.org/t/p/w342' + film.poster_path" alt="">
  </div>
</div>
</template>

<script>
export default {
    name: 'Film',
    props:{
        film: Object,
    },

    methods:{
        numCircles(voto){
            let numCircle = Math.round(voto/2);
            return numCircle;
        }
    }
}
</script>

<style lang="scss" scoped>

.fas.fa-star{
    color: rgba(255, 217, 0, 0.659);
}
ul{
    list-style-type: none;
}
.voto{
    display: flex;
}

.films{
    position: relative;
    display: inline-block;
}

.film{
    position: absolute;
    width: 342px;
    color: white;
    display: block;
    &:hover{

    }
}

.film_img{
    &:hover{
        background-color:#434343;
        z-index: 999;
    }
}



</style>