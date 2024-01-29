<template>
        <div class="generos">
            <h1 class="title" @click="changeView('all')">M<i class="fa-solid fa-clapperboard"></i>VIES</h1>
            <div class="routes">
                <h1>GENEROS</h1>
                <div v-for="pelicula in peliculasTitles" :key="pelicula">
                    <a href="#" @click="changeView(pelicula)">{{ pelicula }}</a>
                </div>
            </div>
            <div class="icon">
                <router-link to="/"><i class="fa-solid fa-right-from-bracket" ></i></router-link>
            </div>
        </div>
</template>
<script>
import FilmsComponent from './FilmsComponent.vue';
import { peliculas } from '@/peliculas';
export default{
    data(){
        return{
            peliculasTitles:Object.keys(peliculas[0])
        }
    },
    methods:{
        changeView(film){
            FilmsComponent.methods.change(film)
        }
    }
}
</script>
<style lang="sass" scoped>

.generos
    width: 22%
    height: 100vh
    display: flex
    flex-direction: column
    align-items: center
    background: #393636

    h1
        color: white
    
        &:hover
            cursor: pointer

    a
        text-decoration: none
        color: white



.title
    font-size: 60px

    i
        color: red

.routes
    width: 100%
    height: 400px
    display: flex
    flex-direction: column
    align-items: center
    justify-content: space-around
    margin-top: 120px

    h1
        font-size: 30px

    a
        text-decoration: none
        color: white
        font-size: 20px
        transition: 0.5s

        &:hover
            color: red
            text-decoration-line: underline

.icon
    height: 300px
    display: flex
    align-items: center
    justify-content: center
    font-size: 40px

    i
        color: white
</style>




