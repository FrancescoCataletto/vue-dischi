<template>
  <div>
      <h2>{{musicCard.author}}</h2>
      <h3>{{musicCard.genre}}</h3>
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
li{
    color: red;
}
</style>