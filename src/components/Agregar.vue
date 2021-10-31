<template>
  <div>

      <!-- Agregando datos a la db -->
      <input type="text" v-model="nombre" placeholder="Agrega una nueva tarea">
      <button v-on:click="agregar">Agregar</button>
  </div>
</template>

<script>

    import {db} from'../db'
    export default {
        name: "Agregar",
        data() {
            return {
                nombre: "",
                terminada: false,
            }
        },
        methods: {
            agregar: function(){
                var nuevo = {nombre: this.nombre, finalizada: this.terminada}
                db.collection('tareas').add(nuevo)
                this.nombre = ""
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>