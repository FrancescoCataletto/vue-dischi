<template>
  <main>
      <div v-if="!isLoaded" id="loader">
          <h2>LOADING YOUR MUSIC, PLEASE WAIT...</h2>
          <div class="lds-ripple"><div></div><div></div></div>
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

export default {
    name: "MainComponent",
    components: { CardComponent },
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
    height: calc(100vh - 80px);
    overflow: auto;
    .container{
        display: flex;
        flex-wrap: wrap;
        height: calc(100vh - 80px);
    }
}

#loader{
    h2{
        color: white;
    }
}

.lds-ripple {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-ripple div {
  position: absolute;
  border: 4px solid #fed;
  opacity: 1;
  border-radius: 50%;
  animation: lds-ripple 1s cubic-bezier(0, 0.2, 0.8, 1) infinite;
}
.lds-ripple div:nth-child(2) {
  animation-delay: -0.5s;
}
@keyframes lds-ripple {
  0% {
    top: 36px;
    left: 36px;
    width: 0;
    height: 0;
    opacity: 0;
  }
  4.9% {
    top: 36px;
    left: 36px;
    width: 0;
    height: 0;
    opacity: 0;
  }
  5% {
    top: 36px;
    left: 36px;
    width: 0;
    height: 0;
    opacity: 1;
  }
  100% {
    top: 0px;
    left: 0px;
    width: 72px;
    height: 72px;
    opacity: 0;
  }
}

</style>