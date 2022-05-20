<template> 
  <div class="container">
    <form @submit.prevent="emitForm"> <!--Hago el envio del form y pongo prevent para que no se refresque la pagina-->
        <div class="row">
            <div class="col col-12">
                <img class="twitter-image" alt="Vue logo" src="../assets/twitter.png">
                <h3 class="twitter-typo">Censo 2022 - twitter</h3>
                <h5 class="twitter-typo-description">La encuesta que nadie pidió pero que todos querían</h5>
              <div class="grid-fields">
                <label for="inputNombre" class="typo-input">Nombre Completo</label>
                <input
                    type="text"
                    class="form-control"
                    id="inputNombre"
                    placeholder="Nombre Completo"
                    v-model="form.nombre"
                    required
                >
                <label for="inputEdad" class="typo-input">Edad</label>
                <input
                    type="text"
                    class="form-control"
                    id="inputEdad"
                    placeholder="Edad"
                    v-model="form.edad"
                    required
                >
                <label for="inputEmail" class="typo-input">Email</label>
                <input
                    type="text"
                    class="form-control"
                    id="inputEmail"
                    placeholder="email@email.com"
                    v-model="form.mail"
                    required
                >
              </div>

            </div>

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
        apellido: '',
        edad: '',
        email: '',
        cursos: [],
        beca: ''
    }
    }),
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

</style>
