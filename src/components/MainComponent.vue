<template>
  <main>
      <div class="container">

      </div>
  </main>
</template>

<script>
export default {
    name: "MainComponent"
}
</script>

<style lang="scss" scoped>
@import "../assets//style/global.scss";

main{
    background-color: rgb(30, 45, 59);
    height: calc(100vh - 80px);
    .container{
        background-color: red;
        height: calc(100vh - 80px);
    }
}
</style>