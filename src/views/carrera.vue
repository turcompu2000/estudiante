<template>
    <div class="container">
        <h1> LISTADO DE CARRERAS PROFESIONALES</h1>
        <table class="table ">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">ID</th>
                    <th scope="col">Carrera</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(carrera,index) in carrera" :key="index">
                <th scope="row">{{index+1}}</th>
                <td>{{carrera.id_Carrera}}</td>
                <td>{{carrera.Carrera}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import axios from 'axios'

export default{
    name:'Estudiantes',
    data(){
        return{
            estudiante:[]
        }
    }, 
    
    mounted(){
        axios
        .get('http://127.0.0.1:8000/api/carerra')
        .then(response=>(this.carrera=response.data.carrera))
    },
}

</script>