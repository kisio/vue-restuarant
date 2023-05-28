<template>
    <Header />
    <h1 class="text-3xl font-bold text-blue-500 py-4">Hello, welcome to the Add Restaurant page</h1>
  
    <form class="add">
      <input type="text" name="name" placeholder="Enter Name" v-model="restuarant.name" class="border rounded-md p-2 mb-4 text-black" />
      <input type="text" name="address" placeholder="Enter Address" v-model="restuarant.address" class="border rounded-md p-2 mb-4 text-black" />
      <input type="text" name="city" placeholder="Enter City" v-model="restuarant.city" class="border rounded-md p-2 mb-4 text-black" />
      <input type="text" name="state" placeholder="Enter State" v-model="restuarant.state" class="border rounded-md p-2 mb-4 text-black" />
      <button @click="addRestuarant" type="button" class="bg-lime-500 text-white font-bold py-2 px-4 rounded">Add New Hotel</button>
    </form>
  </template>
  
  
 <script>
 import Header from './Header.vue'
 import axios from "axios";
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
        async addRestuarant(){
            console.warn(this.restuarant)
            const result=await axios.post("http://localhost:3000/restuarant",{
                name:this.restuarant.name,
                address:this.restuarant.address,
                city:this.restuarant.city,
                state:this.restuarant.state,
            });
            if(result.status==201)
            {
                this.$router.push('/');
            }
            console.warn("result",result)
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