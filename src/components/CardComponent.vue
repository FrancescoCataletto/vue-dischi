<template>
  <div id="card-box">
      <div>
          <img :src="musicCard.poster" alt="IMMAGINE">
          <h2 id="main-title">{{musicCard.title}}</h2>
      </div>
      <div id="info">
          <h2>{{musicCard.author}}</h2>
          <p>{{musicCard.year}}</p>
      </div>
  </div>
</template>

<script>
export default {
    name: "CardComponent",
    props:{
        musicCard: Object
    }
}
</script>

<style lang="scss" scoped>
#card-box{
    width: calc(100% / 5 - 20px);
    background-color: rgb(46, 58, 70);
    margin: 10px;
    text-align: center;
    img{
        width: 100%;
        padding: 15px;
    }
    h2{
        margin: 20px 0;
    }
}

#main-title{
    color: white;
}

#info{
    color: rgb(125, 121, 119);
    padding-bottom: 20px;
}
</style>