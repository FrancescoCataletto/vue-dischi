<template>
  <header>
      <div id="menu" class="container-fluid">
          <div>
              <a href="#"><img src="../assets/style/spotify-logo-png-7053.png" alt=""></a>
          </div>
          <div>
              <select name="" id="" @change="$emit('cambiogenere', genere)" v-model="genere">
                  <option value="" selected>Seleziona un genere</option>
                  <option value="Rock">Rock</option>
                  <option value="Jazz">Jazz</option>
                  <option value="Pop">Pop</option>
                  <option value="Metal">Metal</option>
              </select>

              <select name="" id="" @change="$emit('cambioartista', artista)" v-model="artista">
                  <option value="" selected>Seleziona un artista</option>
                  <option value="Bon Jovi">Bon Jovi</option>
                  <option value="Queen">Queen</option>
                  <option value="Sting">Sting</option>
                  <option value="Steve Gadd Band">Steve Gadd Band</option>
              </select>
          </div>
      </div>
  </header>
</template>

<script>
export default {
    name: "HeaderComponent",
    data(){
        return{
            genere: "",
            artista: ""
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets//style/global.scss";

header{
    height: 80px;
    background-color: rgb(41, 49, 58);
    position: fixed;
    width: 100vw;
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