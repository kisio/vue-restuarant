<template>
    <Header/>
    <h1>Hello, welcome to the Add Restuarant page</h1>
    <form class="add">
        <input type="text" mame="name" placeholder="Enter Name" v-model="restuarant.name"/>
        <input type="text" mame="address" placeholder="Enter Address" v-model="restuarant.address"/>
        <input type="text" mame="city" placeholder="Enter City" v-model="restuarant.city"/>
        <input type="text" mame="state" placeholder="Enter State" v-model="restuarant.state"/>
        <button @click="addRestuarant" type="button">Add New Hotel</button>
    </form>
 </template>
 <script>
 import Header from './Header.vue'
 export default {
     name: 'AddPage',
     components:{
        Header
     },
     data(){
        return{
            restuarant:{
                name:'',
                address:'',
                city:'',
                state:''
            }
        }
     },
     methods:{
        addRestuarant(){
            console.warn(this.restuarant)
        }
     },
     mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({ name: 'SignUp' })
        }
    }
 }
 </script>