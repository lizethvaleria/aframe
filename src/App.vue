<template>
  <div id="app">
    <Escena
      class="w-50"
      :cielo="localizacionActual.cielo"
      :navegadores="localizacionActual.navegadores"
      :cielos="cielos"
      @cambiar="cambiar"
      :video="localizacionActual.video"
      :informacion="localizacionActual.informacion"
    />
  </div>
</template>

<script>
import Escena from "./components/Escena.vue";
const cielos = ["huella.png", "vistafrontal.png"];

const escenas = {
  huella: {
    cielo: "huella.png",
    navegadores: [{ posicion: "-2.6 0 -0.6", hacia: "vistafrontal" }],
  },
 vistafrontal: {
    cielo: "vistafrontal.png",
    navegadores: [{ posicion: "-2.6 0 -0.6", hacia: "huella" }],
  },
  
  
};

export default {
  name: "App",
  data() {
    return {
      localizacionActual: escenas.huella,
      cielos: cielos,
    };
  },
  components: { Escena },
  methods: {
    cambiar: function (hacia) {
      this.localizacionActual = escenas[hacia];
    },
  },
  mounted() {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
