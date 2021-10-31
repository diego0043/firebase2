<template>
  <div>
    <h2>Listado de tareas</h2>

    <!-- mostrando datos de la base de datos y eliminacion-->
    <ul>
        
        <li v-for="(tarea,key) in tareas" :key="key">
            {{tarea.nombre}} <span v-show="tarea.completada">"Terminada"</span> <br>
            <button v-on:click="eliminar(tarea.id)">Eliminar</button>
            <button v-show="!tarea.completada" v-on:click="modificar(tarea)">Terminada</button><br>
        </li>
    </ul>
    <agregar></agregar>

  </div>
</template>

<script>
    import {db} from '../db.js'
    import Agregar from './Agregar.vue'

    export default {
        name: "Listado",
        components: {Agregar},
        data() {
            return {
                tareas: [],
            }
        },
        methods: {
            eliminar: function(id){
                db.collection('tareas').doc(id).delete()
            },
            modificar: function(tarea){
                tarea.completada = true
                db.collection('tareas').doc(tarea.id).set(tarea).then(() =>{
                    console.log("Se actualizo correctamente")
                }).catch((error) =>{
                    console.log("Algo salio mal"+ error)
                })
            }

        },

        firestore: {
            tareas: db.collection('tareas'),
        }
    };
</script>

<style scoped>
    li{
    list-style: none;
    }

</style>
