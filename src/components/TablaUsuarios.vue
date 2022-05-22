<template>
<table class="tabla-contenido">
    <thead>
        <tr>
            <th class="typo-encabezado" scope="col" v-for="(title, i) in titulos" :key="i">{{ title }}</th>
        </tr>
        <tbody>
            <tr :class="tbody(i)" v-for="(user, i) in usuarios" :key="i">
                <td>{{user.nombre}}</td>
                <td>{{user.edad}}</td>
                <td>{{user.email}}</td>
                <td>{{user.estacion}}</td>
                <td>{{user.pandulce}}</td>
                <td>{{user.papelhigienico}}</td>
                <td>{{user.numeros}}</td>
                <td>{{user.opcionSeleccionada}}</td>
            </tr>
        </tbody>
    </thead>
    
</table>
  
</template>

<script>
export default {
    props:{
        usuarios:{
            type: Array
        }   
    },
    data: () => ({
        titulos: ["Nombre","Edad","Email","Estaciones","Pan Dulce","Papel Higienico","Dos Cero Dos Cuatro","Acompañamiento Mate"]
    }),
    methods:{
        tbody(i){
             return i % 2 == 0 ? 'typo-contenido1' : 'typo-contenido2' 
        }
    }
}
</script>

<style>
.tabla-contenido{
    margin-top: 3rem;
    display: flex;
    justify-content: center;
    border: 1px solid black;
}
.typo-encabezado{
    font-family: 'Fredoka One', cursive;
    font-size: 20px;
    margin: 2rem 0;
    background: lightblue;
    padding: 0.5rem 3.63rem;
}
.typo-contenido1{
    font-family: 'Fredoka One', cursive;
    font-size: 18px;
    background: white;  
}
.typo-contenido2{
    font-family: 'Fredoka One', cursive;
    font-size: 18px;
    background: rgb(182, 181, 181);
}
td{
    padding: 0.5rem 0;
}

</style>