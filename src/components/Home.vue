<template>
    <h1>Hello, welcome to the home page</h1>
 </template>
 <script>
 export default {
     name: 'HomePage',
     mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({ name: 'SignUp' })
        }
    }
 }
 </script>