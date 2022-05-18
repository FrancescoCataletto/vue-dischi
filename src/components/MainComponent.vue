<template>
  <main>

    <HeaderComponent />

      <div v-if="!isLoaded">
          <LoadingComponent />
      </div>
      <div class="container" v-else>
          <CardComponent v-for="(card, index) in musicArray" 
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
      isLoaded: false
    }
  },
  methods: {
    getAPI(){
      axios.get(this.baseURL)
      .then(res => {
        this.musicArray = res.data.response;
        this.isLoaded = !this.isLoaded
      })
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