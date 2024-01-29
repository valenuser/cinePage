<template>
    <section>
        <NavComponent/>
        <FilmsComponent/>
    </section>
</template>
<script>
import { peliculas } from '@/peliculas';
import FilmsComponent from '@/components/FilmsComponent.vue';
import NavComponent from '@/components/NavComponent.vue';
export default{
    components:{
        FilmsComponent,
        NavComponent
    },
    data(){
        return{
            peliculasTitles:Object.keys(peliculas[0])
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



            
</style>