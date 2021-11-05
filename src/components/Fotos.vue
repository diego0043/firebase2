<template>
  <div>
    <input @change="clickImagen($event)" type="file" accept="image/*" id=""><br><br>
    <v-btn @click="subirImagen" elevation="2" depressed>Subir</v-btn> <br><br>
    <v-btn @click="cargarImagenes2" elevation="2" depressed>Cargar Imagenes</v-btn>

    <v-container v-if="imagenDesc != false">
       <v-container v-for="img in imagenes" v-bind:key="img">
            <img :src="img" alt="" width="500px">
       </v-container>
    </v-container>
        
    
    <v-container>

    </v-container>
  </div>
</template>

<script>
import {storage} from '../firebase'
const ref = storage.ref()
export default {
    
    data() {
        return {
            imagenes: [],
            imagen: null,
            imagenDesc: false,
        }
    },
    methods: {
        clickImagen(e){
            this.imagen = e.target.files[0]
            console.log(this.imagen)
        },
        subirImagen(){
            //crear referencia de donde queremos subirla 
            const refImg = ref.child('Imagenes/'+this.imagen.name)
            const metaData = {contentType: 'img/jpeg'}
            refImg.put(this.imagen, metaData).then(e =>{
                console.log(e)
            })
            
        },

        cargarImagenes(){
            ref.child('Imagenes/profile_n.jpg').getDownloadURL().then((url) => {
                this.imagenDesc = url
            })
        },

        cargarImagenes2(){
            ref.child('/Imagenes').listAll()
            .then((res) => {
                res.items.map((item) => {
                    ref.child(item.location.path_).getDownloadURL()
                    .then((url) => {
                        this.imagenDesc = true
                        this.imagenes.push(url)
                        console.log(this.imagenes)
                    })
                })
            })

        }


    },
};
</script>

<style></style>
