<template>
  <main>
      <div class="container">
          <CardComponent v-for="(card, index) in musicArray" 
                        :key="`card-${index}`"
                        :musicCard="card"/>
      </div>
  </main>
</template>

<script>
import CardComponent from './CardComponent.vue';
import axios from "axios";

export default {
    name: "MainComponent",
    components: { CardComponent },
    data(){
    return{
      baseURL: "https://flynn.boolean.careers/exercises/api/array/music",
      musicArray: []
    }
  },
  methods: {
    getAPI(){
      axios.get(this.baseURL)
      .then(res => {
        this.musicArray = res.data.response;
        console.log(res.data.response)
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
    height: calc(100vh - 80px);
    .container{
        height: calc(100vh - 80px);
    }
}
</style>