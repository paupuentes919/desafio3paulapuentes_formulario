<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <formulario-twitter/>
  </div>
</template>

<script>
import FormularioTwitter from './components/FormularioTwitter.vue'

export default {
  name: 'App',
  components: {
    FormularioTwitter
  },
  data: () => ({
  form: {
    nombre: '',
    apellido: '',
    edad: '',
    email: '',
    cursos: [],
    beca: ''
  }
 }),
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
