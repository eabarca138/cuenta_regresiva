<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />


  <div class="contenedor">
<!--     <div class="minutos">{{minutos}}</div> -->
    <div class="segundos" :class="{ red: segundos === 0}">{{segundos}}</div>

    <div>
    <button class="btn start" @click="start"><i class="far fa-play-circle"></i></button>
    <button class="btn pause" @click="pause"><i class="far fa-pause-circle"></i></button>
    <button class="btn stop" @click="stop"><i class="far fa-stop-circle"></i></button>
    </div>

    <button class="btn btn-t" v-for="boton in arrBotones" :key="boton.nombre" @click="botonesTiempo(boton.valor)">{{boton.nombre}}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data(){
    return{
      segundos: 20,
/*       minutos: 0, */
      intervalo: "",
      arrBotones: [
        {
          nombre: "3s",
          valor: 3,
          },
        {
          nombre:"1m",
          valor: 60,
        },
        {
          nombre: "5m",
          valor: 300,
        },
        {
          nombre: "10m",
          valor: 600,
        },
        {
          nombre: "30m",
          valor: 1800,
        }
      ],

    }
  },

  watch:{
    segundos(v){
      if(v === 0) this.pause()
/*       if (v > 59) this.segundos === 0; 
       if (v === 0) this.minutos--
       if (v > 59) this.minutos = (this.segundos/60) - 1;
       if (v === -1) this.segundos = 59; */
    }
  },



  methods: {
    start() {
      this.intervalo = setInterval(() => {
        this.segundos--
      }, 1000);
    },
    pause(){
      clearInterval(this.intervalo)
    },
    stop(){
      this.segundos = 0
    },
  botonesTiempo(v){
    this.segundos = v
  }
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.contenedor{
  display: inline-block;
  box-shadow: 5px 5px 8px 10px #888888;
}


.btn{
  margin: 1rem 1rem;
  background-color: #fff;
  border-style: none;
  cursor: pointer;
}

.btn-t{
  font-size: 2rem;
  border-radius: 5px ;
  border: solid 3px black;
}

.start{
  font-size: 3rem;
  color: green;
}

.pause{
  font-size: 3rem;
  color: blue;
}

.stop{
  font-size: 3rem;
  color: red;
}

.segundos{
  font-size: 5rem;
}

.red{
  color: red;
}

</style>
