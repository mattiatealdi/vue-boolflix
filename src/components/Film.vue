<template>
  <div class="film">
      <ul>
          <li v-if="film.name == undefined">Titolo: {{ film.title }} </li> <li v-if="film.title == undefined ">Titolo: {{ film.name }}</li>
          <li v-if="film.original_name == undefined">Titolo originale: {{ film.original_title}}</li><li v-if="film.original_title == undefined "> Titolo originale: {{ film.original_name }}</li>
          <li v-if="film.original_language == 'it'">Lingua: {{ film.original_language }} <country-flag country='it' size='small'/></li>
          <li v-if="film.original_language =='en'">Lingua: {{film.original_language}} <country-flag country='gb' size='small'/> </li>
          <li>Voto: {{film.vote_average}} </li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Film',
    props:{
        film: Object,
    }
}
</script>

<style>

</style>