<template>
  <div>
  <img alt="Vue logo" src="./assets/logo.png">
  <componente-paises-comidas></componente-paises-comidas>
  </div>
</template>

<script>
import ComponentePaisesComidas from './components/ComponentePaisesComidas.vue'


export default {
  name: 'App',
  components: {
    ComponentePaisesComidas
  }
}
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
