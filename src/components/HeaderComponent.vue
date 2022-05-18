<template>
  <header>
      <div id="menu" class="container-fluid">
          <div>
              <a href="#"><img src="../assets/style/spotify-logo-png-7053.png" alt=""></a>
          </div>
          <div>
              <select name="" id="">
                  <option value="Choose" selected>Seleziona un genere</option>
                  <option value="rock">Rock</option>
                  <option value="Jazz">Jazz</option>
                  <option value="Pop">Pop</option>
                  <option value="Metal">Metal</option>
              </select>
          </div>
      </div>
  </header>
</template>

<script>
export default {
    name: "HeaderComponent"
}
</script>

<style lang="scss" scoped>
@import "../assets//style/global.scss";

header{
    height: 80px;
    background-color: rgb(41, 49, 58);
}
#menu{
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 80px;
    img{
        height: 50px;
    }
}
</style>