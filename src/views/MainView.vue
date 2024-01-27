<template>
    <section>
        <div class="generos">
            <h1 class="title">M<i class="fa-solid fa-clapperboard"></i>VIES</h1>
            <div class="routes">
                <h1>GENEROS</h1>
                <div v-for="pelicula in peliculasTitles" :key="pelicula">
                    <a href="#">{{ pelicula }}</a>
                </div>
            </div>
        </div>
        <FilmsComponent/>
    </section>
</template>
<script>
import { peliculas } from '@/peliculas';
import FilmsComponent from '@/components/FilmsComponent.vue';
export default{
    components:{
        FilmsComponent
    },
    data(){
        return{
            peliculasTitles:Object.keys(peliculas[0])
        }
    },
    mounted(){
        console.log(this.peliculasTitles);
    }
}
</script>
<style lang="sass" scoped>
section
    width: 100%
    height: 100vh
    background: black
    display: flex

.generos
    width: 22%
    height: 100vh
    display: flex
    flex-direction: column
    align-items: center
    background: #393636

    h1
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

            
</style>