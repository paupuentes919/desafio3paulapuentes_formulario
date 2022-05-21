<template> 
  <div class="container">
    <form @submit.prevent="emitFormulario"> <!--Hago el envio del form y pongo prevent para que no se refresque la pagina-->
        <div class="row">
            <div class="col col-12">
                <img class="twitter-image" alt="Vue logo" src="../assets/twitter.png">
                <h3 class="twitter-typo">Censo 2022 - twitter</h3>
                <h5 class="twitter-typo-description">La encuesta que nadie pidió pero que todos querían</h5>
              <div class="grid-fields">
                <!------------------------------ NOMBRE COMPLETO ------------------------------>
                <label for="inputNombre" class="typo-input">Nombre Completo
                  <span v-if="!validar.nombre && form.nombre">✅</span> 
                </label>
                <input
                    type="text"
                    id="inputNombre"
                    class="form-control"
                    placeholder="Nombre Completo"
                    v-model="form.nombre"
                    @keyup="validarNombre"
                    required
                >
                <span v-if="validar.nombre" class="warning">{{validar.nombre}}</span>
                <!------------------------------------ EDAD ----------------------------------->
                <label for="inputEdad" class="typo-input">Edad
                   <span v-if="!validar.edad && form.edad">✅</span> 
                </label>
                <input
                    type="text"
                    class="form-control"
                    id="inputEdad"
                    placeholder="Edad"
                    v-model="form.edad"
                    @keyup="validarEdad"
                    required
                >
                <span v-if="validar.edad" class="warning">{{validar.edad}}</span>
                <!------------------------------------ EMAIL ---------------------------------->
                <label for="inputEmail" class="typo-input">Email
                  <span v-if="!validar.email && form.email">✅</span> 
                </label>
                <input
                    type="text"
                    class="form-control"
                    id="inputEmail"
                    placeholder="email@email.com"
                    v-model="form.email"
                    @keyup="validarEmail"
                    required
                >
                <span v-if="validar.email" class="warning">{{validar.email}}</span>
              </div>
              <!------------------------------------ ENCUESTA ----------------------------------->
              <div class="col col-2">
                <h4 class="typo-input">1 - Estaciones</h4>
                <div class="row-questions">
                  <div class="form-check">
                    <input
                      type="radio"
                      name="Team Verano"
                      class="form-check-input"
                      value="Team Verano"
                      v-model="form.estacion"
                    >
                    <label for="Team Verano" class="typo-input-questions">Team Verano</label>
                  </div>
                  <div class="form-check">
                    <input
                      type="radio"
                      name="Team Invierno"
                      class="form-check-input"
                      value="Team Invierno"
                      v-model="form.estacion"
                    >
                    <label for="TeamInvierno" class="typo-input-questions">Team Invierno</label>
                  </div>
                </div>
              </div>
              <div class="col col-2">
                <h4 class="typo-input">2 - Pan Dulce</h4>
                <div class="row-questions">
                  <div class="form-check">
                    <input
                      type="radio"
                      name="Con Chocolate"
                      class="form-check-input"
                      value="Con Chocolate"
                      v-model="form.pandulce"
                    >
                    <label for="Con Chocolate" class="typo-input-questions">Con Chocolate</label>
                  </div>
                  <div class="form-check">
                    <input
                      type="radio"
                      name="Con Frutas Abrillantadas"
                      class="form-check-input"
                      value="Con Frutas Abrillantadas"
                      v-model="form.pandulce"
                    >
                    <label for="Con Frutas Abrillantadas" class="typo-input-questions">Con Frutas Abrillantadas</label>
                  </div>
                </div>
              </div>
              <div class="col col-2">
                <h4 class="typo-input">3 - Papel Higienico</h4>
                <div class="row-questions">
                  <div class="form-check">
                    <input
                      type="radio"
                      name="Cuelga por delante"
                      class="form-check-input"
                      value="Cuelga por delante"
                      v-model="form.papelhigienico"
                    >
                    <label for="Cuelga por delante" class="typo-input-questions">Cuelga por delante</label>
                  </div>
                  <div class="form-check">
                    <input
                      type="radio"
                      name="Cuelga por detras"
                      class="form-check-input"
                      value="Cuelga por detras"
                      v-model="form.papelhigienico"
                    >
                    <label for="Cuelga por detras" class="typo-input-questions">Cuelga por detras</label>
                  </div>
                </div>
              </div>
              <div class="col col-2">
                <h4 class="typo-input">4 - Cual es la opción correcta de "Dos Cero Dos Cuatro" (Valido varias opciones) ?</h4>
                <div class="row-questions">
                  <div class="form-check">
                    <input
                      type="checkbox"
                      id="2024"
                      class="form-check-input"
                      value="2024"
                      v-model="form.numeros"
                    >
                    <label for="2024" class="typo-input-questions">2024</label>
                  </div>
                  <div class="form-check">
                    <input
                      type="checkbox"
                      id="0044"
                      class="form-check-input"
                      value="0044"
                      v-model="form.numeros"
                    >
                    <label for="0044" class="typo-input-questions">0044</label>
                  </div>
                  <div class="form-check">
                    <input
                      type="checkbox"
                      id="0024"
                      class="form-check-input"
                      value="0024"
                      v-model="form.numeros"
                    >
                    <label for="0024" class="typo-input-questions">0024</label>
                  </div>
                  <div class="form-check">
                    <input
                      type="checkbox"
                      id="2044"
                      class="form-check-input"
                      value="2044"
                      v-model="form.numeros"
                    >
                    <label for="2044" class="typo-input-questions">2044</label>
                  </div>
                </div>
              </div>        
              <div class="row">
                  <h4 class="typo-input">5 - El Mate con qué va acompañado?</h4>
                  <select v-model="form.opcionSeleccionada">
                    <option value="" selected></option>
                    <option class="typo-input-questions" v-for="op in listaOpciones" :value="op.opcion" :key="op.opcion" >{{ op.opcion}}</option>
                  </select>
              </div>
            </div>
        </div> 
        <div class="submit">
          <input
            type="submit"
            class="btn-submit"
            value="ENVIAR">
        </div>  
    </form>
  </div>
</template>

<script>
export default {
  name: 'FormularioTwitter',
  data: () => ({
    form: {
        nombre: '',
        edad: '',
        email: '',
        estacion: '',
        pandulce: '',
        papelhigienico:'',
        numeros: [],
        opcionSeleccionada: '',
    },
    validar:{
      nombre: '',
      edad: '',
      email: ''
    },
    listaOpciones: [
                {
                    id: 1,
                    opcion: 'Churros'
                },
                {
                    id: 2,
                    opcion: 'Facturas'
                },
                {
                    id: 3,
                    opcion: 'Bizcochitos'
                },
                {
                    id: 4,
                    opcion: 'Galletitas'
                },
                {
                    id: 5,
                    opcion: 'Tortitas negras'
                },
            ],        
  }),
  methods:{
    emitFormulario(){
      //console.log("formulario enviado", this.form);
      this.$emit('submit-formulario',this.form);
      this.resetFormulario();
    },
    validarNombre(){
      let regexNombre =/[a-zA-Z]{2,}\s+[a-zA-Z]{2,}/ // [] -- un rango posible de caracteres | [a-zA-Z] -- Cualquier letra en mayúsculas o minúsculas | {2,} -- el caracter aparece al menos 2 veces | \s -- espacio
    
      if (this.form.nombre && regexNombre.test(this.form.nombre)){
        this.validar.nombre = ''; 
      }
      else{
        this.validar.nombre = 'Por favor, ingrese su nombre completo'
      }
    }, 
    validarEdad(){   
      let regexEdad = /[0-9]/
      if (this.form.edad && regexEdad.test(this.form.edad)){
        this.validar.edad = ''; 
      }
      else{
        this.validar.edad = 'Por favor, ingrese un numero'
      }
    },
    validarEmail(){
      let regexEmail =/[\w._%+-]+@[\w.-]+\.[a-zA-Z]{2,4}/ 
    
      if (this.form.email && regexEmail.test(this.form.email)){
        this.validar.email = ''; 
      }
      else{
        this.validar.email = 'Por favor, ingrese un mail valido'
      }
    },
    resetFormulario(){
       this.form.nombre = '';
       this.form.edad = '';
       this.form.email = '';
       this.form.estacion = '';
       this.form.pandulce = '';
       this.form.papelhigienico = '';
       this.form.numeros = [];
       this.form.opcionSeleccionada = '',
       this.validar.nombre = '';
       this.validar.edad = '';
       this.validar.email = '';
    
    }
  }, 
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Fredoka+One&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
a {
  color: #42b983;
}
label {
  margin-left: 0.5em !important;
}
.twitter-image{
    width: 12rem;
}
.twitter-typo{
    font-family: 'Fredoka One', cursive;
    font-size: 50px;
    margin-top: 0;
    margin-bottom: 1rem;
}
.twitter-typo-description{
    font-family: 'Fredoka One', cursive;
    font-size: 20px;
    margin-top: 0;
    margin-bottom: 3.5rem;
}
.typo-input{
    font-family: 'Fredoka One', cursive;
    font-size: 25px;
    margin-bottom: 1rem;
}
.typo-input-questions{
  font-family: 'Fredoka One', cursive;
    font-size: 25px;
    margin-bottom: 1rem;
    margin-right: 1rem;

}
.grid-fields{
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 0 40%;
}
input{
  height: 30px;
  font-family: 'Roboto', sans-serif;
  font-size: 15px;
}
.form-control{
  margin-bottom: 3rem;
}
.row-questions{
  display: flex;
  justify-content: center;
}
.warning{
  color: red;
  font-size: small;
  margin-top: -3rem;
  margin-bottom: 2rem;
}
.submit{
  margin-top: 10rem;
}
.btn-submit{
  font-family: 'Fredoka One', cursive;
  font-size: 30px;
  width: 20rem;
  height: 5rem;
  background: rgb(62, 171, 207);
}

</style>
