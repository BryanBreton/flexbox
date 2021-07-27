<template>
<div class="body">
  <div class="topbar">oui</div>
  <div class="wrapper">
    <div class="nav">
      <div class="nav1" @click="addSeance(1)">Seance 1</div>
      <div class="nav2" @click="addSeance(2)">Seance 2</div>
      <div class="nav3" @click="console.log('non')">Seance 3</div>
      <div class="nav4">Seance 4</div>
    </div>
    <div class="content">
      <v-card>
        <v-card-title>
          {{seance.numeroSeance}}
        </v-card-title>
        <v-card-content>
          <v-img :src="seance.exercices[0].url"></v-img>
        </v-card-content>
        <v-card-footer>
          oui
        </v-card-footer>
      </v-card>
    </div>
  </div>
  
  <div class="footer">oui4</div>
</div>
</template>

<script>
import seances from "../services/seances.json"
export default {
  name: 'Home',
  data : () => {
    return {
      seance: {"a":"a"},
      seances: [{a: 1}, {a: 2}]
    }
  },
  methods: {
    addSeance(numeroSeance) {
      this.seance = seances.filter(s => s.numeroSeance === numeroSeance)[0]
      console.log(this.seance.exercices[0].url)
    }
  },
  components: {},
};
</script>
<style>
.body{
  background-color:black;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.wrapper{
  display: flex;
  flex: 1;
}
.topbar{
  background-color: green;
  min-height: 10vh;
}
.nav{
  background-color:red;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  flex: 1;
}
.nav>*{
  flex: 1;
  background-color: #fff;
}
.nav>*:hover{
  flex: 2 !important;
  background-color: #fff;
}
.nav1{
  background-color: blue;
}
.nav2{
  background-color: cyan;
}
.nav3{
  background-color: magenta;
}
.nav4{
  background-color: brown;
}
.content{
  background-color:yellow;
  flex: 3;
}
.footer{
  background-color: purple;
  min-height: 10vh;
}
</style>
