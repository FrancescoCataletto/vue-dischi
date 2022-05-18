<template>
  <main>

    <HeaderComponent @cambiogenere="cambio"
                     @cambioartista= "cambioartista"/>

      <div v-if="!isLoaded">
          <LoadingComponent />
      </div>
      <div class="container" v-else>
          <CardComponent v-for="(card, index) in selectMusicGenre" 
                        :key="`card-${index}`"
                        :musicCard="card"/>
      </div>
  </main>
</template>

<script>
import CardComponent from './CardComponent.vue';
import axios from "axios";
import LoadingComponent from "./LoadingComponent.vue";
import HeaderComponent from './HeaderComponent.vue';

export default {
    name: "MainComponent",
    components: { CardComponent, LoadingComponent, HeaderComponent },
    data(){
    return{
      baseURL: "https://flynn.boolean.careers/exercises/api/array/music",
      musicArray: [],
      isLoaded: false,
      musicGenre: "",
      currentArtist: ""
    }
  },
  methods: {
    getAPI(){
      axios.get(this.baseURL)
      .then(res => {
        this.musicArray = res.data.response;
        this.isLoaded = !this.isLoaded
      })
    },
    cambio(selected){
      this.musicGenre = selected
    },
    cambioartista(artist){
      this.currentArtist = artist
    }
  },

  computed: {
    selectMusicGenre(){
      let filteredArray = [];
      if(this.musicGenre.length === 0 && this.currentArtist.length === 0){
        filteredArray = this.musicArray
      }else if(this.musicGenre.length !== 0){
        filteredArray = this.musicArray.filter(music => {
          return music.genre.toUpperCase().includes(this.musicGenre.toUpperCase())
        })
      }else if(this.currentArtist.length !== 0){
        filteredArray = this.musicArray.filter(artist =>{
          return artist.author.toUpperCase().includes(this.currentArtist.toUpperCase())
        })
      }
      return filteredArray;
    }
  },

  mounted(){
    this.getAPI()
  }
}
</script>

<style lang="scss" scoped>
@import "../assets//style/global.scss";

main{
    background-color: rgb(30, 45, 59);
    height: 100vh;
    overflow: auto;
    .container{
        display: flex;
        flex-wrap: wrap;
        margin-top: 100px;
    }
}

</style>