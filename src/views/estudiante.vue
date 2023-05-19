<template>
    <div class="container">
        <h1> LISTADO DE ESTUDIANTES
            <button @click="newEstudiantes()"
            class="btn btn-success mx-2">
            <font-awesome-icon icon="plus" />  
            </button>
        </h1>
        <table class="table ">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">ID</th>
                    <th scope="col">Nombre estudiante</th>
                    <th scope="col">Apellido</th>
                    <th scope="col">Carrera</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(estudiante,index) in estudiante" :key="index">
                <th scope="row">{{index+1}}</th>
                <td>{{estudiante.id_Estudiante}}</td>
                <td>{{estudiante.Nomb_Estudiante}}</td>
                <td>{{estudiante.Apellido}}</td>
                <td>{{estudiante.Carrera}}</td>
                <td></td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
import axios from 'axios'

export default{
    name:'Estudiante',
    data(){
        return{
            estudiante:[]
        }
    },
    mounted(){
        axios
        .get('http://127.0.0.1:8000/api/estudiante')
        .then(response=>(this.estudiante=response.data.estudiante))
    },
}
</script>