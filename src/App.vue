<template>
  <div id="app">
    <formulario-twitter
      @submit-formulario="registroUsuarios"/>
    <tabla-usuarios v-if="usuarios.length != 0"
      :usuarios="usuarios"/>
  </div>
</template>

<script>

import FormularioTwitter from './components/FormularioTwitter.vue'
import TablaUsuarios from './components/TablaUsuarios.vue';

export default {
  name: 'App',
  components: {
    FormularioTwitter,
    TablaUsuarios  
  },
  data:() => ({
    usuarios: []
  }),
  methods:{
    registroUsuarios(formulario){
      let nuevoUsuario = {...formulario};
      this.usuarios.push(nuevoUsuario);
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
