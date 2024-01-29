<template>
<section>
<div class="title">
    <router-link to="/main"><h1>M<i class="fa-solid fa-clapperboard"></i>VIES</h1></router-link>
    <router-view></router-view>
</div>
<div class="data">
    <div class="imageData">
        <img :src="pelicula.picture" alt="">
    </div>
    <div class="info">
        <h1>{{ pelicula.nombre }}</h1>
        <p>Valoracion de la pelicula: {{ valorar }} </p>
        <div class="valoracion">
            <p>Valora esta pelicula:</p>
            <div>
                <button @click="restar">-</button>
                <input type="number" name="" id="" v-model="valoracion" min="1" max="5" readonly>
                <button @click="sumar">+</button>
            </div>
            <button class="send"  @click="add">Enviar</button>
        </div>
    </div>
</div>
</section>
</template>
<script>
import Swal from 'sweetalert2'
import { peliculas } from '@/peliculas';
export default{
    data(){
        return{
            section:this.$route.params.section,
            pelicula:peliculas[0][this.$route.params.section].find(el => el.id == this.$route.params.id),
            valoracion: 1,
            indice: 0
        }
    },
    mounted(){
        peliculas[0][this.$route.params.section].map(el =>{
                if(el.nombre.indexOf(peliculas[0][this.$route.params.section].find(el => el.id == this.$route.params.id).nombre) == 0){
                    this.indice = peliculas[0][this.$route.params.section].indexOf(el)
                }
            })
    },
    methods:{
        sumar(){
            if(this.valoracion < 5){
                this.valoracion = this.valoracion +1
            }
        },
        restar(){
            if(this.valoracion > 1){
                this.valoracion = this.valoracion -1
            }
        },
        add(){
            peliculas[0][this.$route.params.section][this.indice].valoraciones_users.push(this.valoracion)
            this.valoracion = 1
            Swal.fire({
                icon: "success",
                title: "Genial!",
                text: "Se ha enviado con exito tu valoracion"
            });
        }
    },
    computed:{
        valorar(){
            if(this.pelicula.valoraciones_users.length == 0 || this.pelicula.valoraciones_users.length == 1){
                return 1
            }
            let data_valoracion = 0
            this.pelicula.valoraciones_users.forEach(element => {
                data_valoracion = data_valoracion + element
            });

            let final = data_valoracion / 5

            peliculas[0][this.$route.params.section][this.indice].valoracion = final

            return this.pelicula.valoracion
        }
    }
}
</script>
<style lang="sass" scoped>
section
    width: 100%
    height: 100vh
    background: black
    display: flex
    align-items: center
    justify-content: center
    flex-direction: column
    p
        color: white

    .title
        width: 100%
        height: 10vh
        display: flex
        align-items: center
        justify-content: center
        a
            text-decoration: none
        h1
            color: white
            font-size: 70px

        i
            color: red
    .data
        width: 100%
        height: 90vh
        display: flex
        align-items: center
        justify-content: center




    .imageData
        width: 50%
        display: flex
        align-items: center
        justify-content: center
        overflow: hidden
        img
            width: 840px
            height: 70vh
            border-radius: 5px
            margin-left: 120px
            margin


    .info
        display: flex
        align-items: center
        flex-direction: column
        justify-content: center
        width: 50%

        h1
            color: white
            font-size: 40px

        p
            text-align: start
            margin-top: 50px
            font-size: 25px
            padding: 5px

    .valoracion
        margin-top: 100px
        display: flex
        align-items: center
        justify-content: center
        text-align: start
        flex-direction: column
        p
            font-size: 30px
        button
            height: 30px
            width: 30px
            font-size: 20px
            border: none
            color: white
            background: orange
            border-radius: 50%

            &:hover
                cursor:pointer

        input
            height: 30px
            width: 160px
            text-align: center
            border-radius: 5px
            border: none
            margin-left: 5px
            margin-right: 5px
            outline: none

        .send
            background: red
            border-radius: 5px
            width: 200px
            margin-top: 50px

            &:hover
                background: #FF7C7C

    
</style>