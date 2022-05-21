<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <formulario-twitter
      @submit-formulario="registroUsuarios"/>
    <!-- <formulario-clase/>  -->
  </div>
</template>

<script>
//import Formulario from './components/Formulario.vue'
import FormularioTwitter from './components/FormularioTwitter.vue'
// import FormularioClase from './components/FormularioClase.vue'

export default {
  name: 'App',
  components: {
    FormularioTwitter,
    // FormularioClase
  },
  data:() => ({
    usuarios: []

  }),
  methods:{
    registroUsuarios(form){
      let nuevoUsuario = {...form};
      this.usuarios.push(nuevoUsuario);
      console.log("veo lo que llega",this.usuarios);
    }
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
