<template>
    

  <main>

      <div class="header">
          <h1>BoolFix</h1>
        <input type="text" v-model="query" placeholder="Cosa vuoi cercare?">
        <button type="submitFilm" @click="getFilm('movie')">MOVIES</button>
        <button type="submitTv" @click="getFilm('tv')">TV</button>
        <button type="submit" @click="getFilm('tv'); getFilm('movie');">ALL</button>
    
      </div>
      
      <div class="film_container">
        <Film 
            v-for="film in arrMovies"
            :key="film.id"
            :film="film"
        />

        <Film
            v-for="film in arrTv"
            :key="film.id"
            :film="film"
        />
      </div>

      <!-- <h1 v-if="arrFilms == 0 && arrFilms.length == 0">Nessun risultato trovato</h1> -->
  </main>
</template>

<script>

import axios from 'axios';
import Film from './Film.vue';

export default {
  components: { 
      Film
    },
    name: 'MainComp',

    data(){
        return{
            apiURL: 'https://api.themoviedb.org/3/search/',
            apiKey: '437f527b2395f6578d102747b8be2baa',
            query: '',
            /* arrFilms: [], */
            arrMovies: [],
            arrTv: [],
        }
    },

    methods: {
        getFilm(type){ 
            this.arrMovies = [];
            this.arrTv = [];
            axios.get(this.apiURL+type, {
            params:{
                api_key: this.apiKey,
                query: this.query,
                language: 'it-IT'
            }
        })
        .then(res => {
            if(type === 'movie'){
                this.arrMovies = res.data.results;
            }else{
                this.arrTv = res.data.results;
            }
        })
        .catch(err => {
            console.log(err);
        })

        },
        
        /* getAll(){
            axios.all([
                axios.get(this.apiURL+'movie', {
                    params:{
                        api_key: this.apiKey,
                        query: this.query,
                        language: 'it-IT'
                    }
                }),
                axios.get(this.apiURL+'movie', {
                    params:{
                        api_key: this.apiKey,
                        query: this.query,
                        language: 'it-IT'
                    }
                })
            ])
            .then(axios.spread(function (response1, response2) {
                this.arrTv = response1.data.results;
                //response1 is the result of first call
                //response2 is the result of second call
                this.arrMovies = response2.data.results;
            }))
            .catch(function (error) {

            }); */
        }
        
    }        
</script>

<style lang="scss" scoped>

*{
    margin: 0;
    padding: 0;
}

main{
    
    .header{
        display: flex;
        h1{
            color: red;
            line-height: 100px;
            margin-left: 100px;
        }
        height: 100px;
        background-color: #000000;
        input{
            border: none;
            height: 50px;
            line-height: 100px;
            margin-left: 50%;
            margin-top: 25px;
            width: 400px;
        }
        button{
            height: 50px;
            margin-top: 25px;
            margin-left: 10px;
            padding: 10px;
        }
    }


}



</style>