<template>
    <div class="container">
        <h1> LISTADO DE ESTUDIANTES</h1>
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
                <td>
                    <button @click="deleteEstudiante(estudiante.id_Estudiante)"
                      class="btn btn-danger mx-2">
                      <font-awesome-icon icon="trash" />  
                    </button>
                </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
import axios from 'axios'
import Swal from 'sweetalert2';

export default{
    name:'Estudiantes',
    data(){
        return{
            estudiante:[]
        }
    }, 
    methods:{
        deleteEstudiante(codigo){
            Swal.fire({
                title:`Do you want to delete the estudiantes with id ${codigo}?`,
                showCancelButton: true,
                confirmButtonText: 'Delete',
            }).then((result) => {
                    if(result.isConfirmed){
                        axios.delete(`http://127.0.0.1:8000/api/estudiante/${codigo}`)
                        .then(response => {
                            if (response.data.success){
                                Swal.fire('Deleted!! ', '','success')
                                this.estudiante=response.data.estudiante
                            }
                        })
                    }
                })
        },
    },
    mounted(){
        axios
        .get('http://127.0.0.1:8000/api/estudiante')
        .then(response=>(this.estudiante=response.data.estudiante))
    },
}
</script>