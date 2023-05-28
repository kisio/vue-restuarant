<template>
    <Header/>
    <h1>Hello {{ name }}, welcome to the home page</h1>
    <table class="table">
        <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Address</td>
            <td>City</td>
            <td>State</td>

        </tr>
        <tr v-for="item in restuarant" :key="item.id" >
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.address }}</td>
            <td>{{ item.city }}</td>
            <td>{{ item.state }}</td>
        </tr>
    </table>
 </template> 
 <script>
 import Header from './Header.vue';
 import axios from 'axios';
 export default {
     name: 'HomePage',
     data(){
        return {
            name:'',
            restuarant:[],
        }
     },
     components:{
        Header
     },
    async mounted() {
        let user = localStorage.getItem('user-info');
        this.name=JSON.parse(user).name;
        if (!user) {
            this.$router.push({ name: 'SignUp' })
        }
        let result=await axios.get('http://localhost:3000/restuarant');
        console.warn(result)
        this.restuarant=result.data;

    }
 }
 </script>

 <style>
td{
    border: 1px solid black;
    padding: 10px;
    text-align: center;
    border-radius: 5px;
    margin: 10px;

}
tr{
    border: 1px solid black;
    padding: 10px;
    text-align: center;
    border-radius: 5px;
    margin: 10px;
}
.table{
    border: 1px solid rgb(40, 206, 139);
    padding: 10px;
    text-align: center;
    border-radius: 5px;
    margin: 10px;
}
</style>