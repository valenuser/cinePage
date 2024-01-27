<template>
<section>
    <div class="container">
        <div class="title">
            <h1>M<i class="fa-solid fa-clapperboard"></i>VIES</h1>
        </div>
        <div class="form">
            <div class="containerData">
                <label for="#">Name</label>
                <input type="text" name="" id="" v-model="username">
            </div>
            <div class="containerData">
                <label for="#">Password</label>
                <input type="text" name="" id="" v-model="password">
            </div>
            <button @click="main">Login</button>
        </div>
    </div>
</section>
</template>
<script>
import { users } from '../users'
export default{
    data(){
        return{
            username:'',
            password:''
        }
    },
    methods:{
        main(){
            users.push(
                {
                   username:this.username,
                   password:this.password
                }
            )
            this.$router.push({name:'main'})
        }
    }
}
</script>
<style lang="sass" scoped>
section
    width: 100%
    height: 100vh
    background-image: url('@/assets/fondoLogin.avif')
    display: flex
    align-items: center
    justify-content: center

.container
    background: black
    width: 400px
    height: 400px
    border-radius: 10px
    overflow: hidden



.form
    width: 100%
    height: 250px
    display: flex
    justify-content: space-around
    flex-direction: column
    align-items: center

    button
        width: 140px
        height: 60px
        background: red
        color: white
        border: 1px solid red
        border-radius: 5px
        transition: 0.7s
        letter-spacing: 0.3px
        &:hover
            background: white
            color: red


.containerData
    width: 100%
    height: 200px
    display: flex
    flex-direction: column
    align-items: center
    justify-content: center
    label
        color: lightgrey
        font-size: 20px

    input 
        width: 300px
        height: 30px
        border-radius: 5px
        border: none
        margin-top: 10px
        margin-bottom: 10px
        outline: none
        text-align: center

.title
    width: 100%
    height: 100px
    display: flex
    align-items: center
    justify-content: center
    border-radius: 10px
    i
        color: red

    h1
        font-size: 60px
        color: white
        letter-spacing: 10px



</style>