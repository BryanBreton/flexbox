<template>
<div class="body">
  <div class="topbar">oui</div>
  <div class="wrapper">
    <div class="nav">
      <div class="nav1" @click="addSeance(1)">Seance 1</div>
      <div class="nav2" @click="addSeance(2)">Seance 2</div>
      <div class="nav3" @click="console.log('non')">Seance 3</div>
      <div class="nav4">4</div>
    </div>
    <div class="content">
      <div v-if="seance.exercices">{{seance.exercices[indice].nom}}</div>
      <div v-else>numeros</div>
      <div class="infos" v-if="seance.exercices">
        <div class="repetitions">Repetitions : {{seance.exercices[indice].repetitions}}</div>
        <div class="poids">Poids : {{seance.exercices[indice].poids}}</div>
        <div class="series">Series : {{seance.exercices[indice].series}}</div>
      </div>
      <div class="infos" v-else>
        test
      </div>
      <div class="imageCard" v-if="seance.exercices">
        <v-img :src="seance.exercices[indice].url"></v-img>
      </div>
      <div class="imageCard" v-else></div>
      <div class="backContent">
        <v-btn @click="precedent()">Precedent</v-btn>
        <v-btn @click="suivant()">Suivant</v-btn>
      </div>
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
      seance: {},
      indice: 0
    }
  },
  methods: {
    addSeance(numeroSeance) {
      this.seance = seances.filter(s => s.numeroSeance === numeroSeance)[0]
      console.log(this.seance)
    },
    precedent(){
      this.indice === 0 ? this.indice : this.indice = this.indice - 1
    },
    suivant(){
      this.indice === this.seance.exercices.length ? this.indice : this.indice = this.indice + 1
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
  display: flex;
  flex-direction:column;
}
.infos{
  background-color: green;
  flex: 1;
  display: flex;
}
.infos>*{
  flex: 1;
}
.imageCard{
  flex: 9
}
.backContent{
  display: flex;
}
.backContent>*{
  flex: 1;
}
.footer{
  background-color: purple;
  min-height: 10vh;
}
</style>
