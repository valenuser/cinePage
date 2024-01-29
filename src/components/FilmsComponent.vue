<template>
    <div class="data all">
        <div v-for="categoria in categorias" :key="categoria" class="carril">
            <h1>{{ categoria }}</h1>
            <div class="images">
                <div v-for="pelicula in peliculas[categoria]" :key="pelicula">
                    <img :src="pelicula.picture" alt="" @click="seeFilm(pelicula.id,categoria)">
                    <p>Valoracion</p>
                    <p>{{ pelicula.valoracion }}</p>
                </div>

            </div>
        </div>
    </div>
    <div class='terror data'>
        <div class="carril">
            <h1>Terror</h1>
            <div class="images">
                <div v-for="pelicula in peliculas['terror']" :key="pelicula.id">
                    <img :src="pelicula.picture" alt="" @click="seeFilm(pelicula.id,'terror')">
                    <p>Valoracion</p>
                    <p>{{ pelicula.valoracion }}</p>
                </div>

            </div>
        </div>
    </div>
    <div class='accion data'>
        <div class="carril">
            <h1>accion</h1>
            <div class="images">
                <div v-for="pelicula in peliculas['accion']" :key="pelicula.id">
                    <img :src="pelicula.picture" alt="" @click="seeFilm(pelicula.id,'accion')">
                    <p>Valoracion</p>
                    <p>{{ pelicula.valoracion }}</p>
                </div>

            </div>
        </div>
    </div>
    <div class='comedia data'>
        <div class="carril">
            <h1>Terror</h1>
            <div class="images">
                <div v-for="pelicula in peliculas['comedia']" :key="pelicula.id">
                    <img :src="pelicula.picture" alt="" @click="seeFilm(pelicula.id,'comedia')">
                    <p>Valoracion</p>
                    <p>{{ pelicula.valoracion }}</p>
                </div>

            </div>
        </div>
    </div>
</template>
<script>
import { peliculas } from '@/peliculas';
export default{
    data(){
        return {
            peliculas:peliculas[0],
            categorias:Object.keys(peliculas[0])
        }
    },
    methods:{
        seeFilm(id,name){
            this.$router.push({name:"film",params:{section:name,id:id}})
        },
        change(newParam){
            if(newParam == 'terror'){
                document.getElementsByClassName('all')[0].style = "display:none"
                document.getElementsByClassName('comedia')[0].style = "display:none"
                document.getElementsByClassName('terror')[0].style = "display:flex"
                document.getElementsByClassName('accion')[0].style = "display:none"
            }else if(newParam == 'accion'){
                document.getElementsByClassName('all')[0].style = "display:none"
                document.getElementsByClassName('comedia')[0].style = "display:none"
                document.getElementsByClassName('terror')[0].style = "display:none"
                document.getElementsByClassName('accion')[0].style = "display:flex"
            }else if(newParam == 'comedia'){
                document.getElementsByClassName('all')[0].style = "display:none"
                document.getElementsByClassName('comedia')[0].style = "display:flex"
                document.getElementsByClassName('terror')[0].style = "display:none"
                document.getElementsByClassName('accion')[0].style = "display:none"
            }else{
                document.getElementsByClassName('all')[0].style = "display:flex"
                document.getElementsByClassName('comedia')[0].style = "display:none"
                document.getElementsByClassName('terror')[0].style = "display:none"
                document.getElementsByClassName('accion')[0].style = "display:none"
            }
        }
    }
}
</script>
<style lang="sass" scoped>
section
    width: 78%
    height: 100vh
h1
    color: white
    font-size: 30px
    margin-bottom: 5px

.data
    width: 100%
    display: flex
    flex-direction: column
    justify-content: space-around
    text-align: center


.carril
    width: 100%
    height: 300px
    display: flex
    flex-direction: column
    img
        width: 340px
        height: 200px
        border-radius: 10px

.images
    width: 100%
    align-items: center
    justify-content: space-around
    display: flex

    p
        color: white

    img
        &:hover
            cursor: pointer

.all
    display: flex
.terror
    display: none
.accion
    display: none
.comedia
    display: none
</style>