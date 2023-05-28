<template>
    <Header/>
    <h1>Hello, welcome to the Add Restuarant page</h1>
 </template>
 <script>
 import Header from './Header.vue'
 export default {
     name: 'AddPage',
     components:{
        Header
     },
     mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({ name: 'SignUp' })
        }
    }
 }
 </script>