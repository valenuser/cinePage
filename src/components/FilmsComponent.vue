<template>
    <div v-if="param == ''" class="data" >
        <div v-for="categoria in categorias" :key="categoria" class="carril">
            <h1>{{ categoria }}</h1>
            <div class="images">
                <div v-for="pelicula in peliculas[categoria]" :key="pelicula">
                    <img :src="pelicula.picture" alt="">
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
            param:'',
            peliculas:peliculas[0],
            categorias:Object.keys(peliculas[0])
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
</style>