<template>
    <div>
      <Header />
      <h1 class="text-4xl font-bold text-black py-8">Hello {{ name }}, welcome to the home page</h1>
      <div class="container mx-auto">
        <table class="table center bg-white">
          <tr class="bg-yellow-200">
            <th class="py-4">ID</th>
            <th class="py-4">Name</th>
            <th class="py-4">Address</th>
            <th class="py-4">City</th>
            <th class="py-4">State</th>
            <th class="py-4">Action</th>
          </tr>
          <tr v-for="item in restuarant" :key="item.id">
            <td class="py-5">{{ item.id }}</td>
            <td class="py-5">{{ item.name }}</td>
            <td class="py-5">{{ item.address }}</td>
            <td class="py-5">{{ item.city }}</td>
            <td class="py-5">{{ item.state }}</td>
            <td class="py-2">
              <router-link :to="'/update/' + item.id" class="text-blue-500 px-4 py-2 rounded bg-blue-200 mr-2">Update</router-link>
              <button v-on:click="deleteRestuarant(item.id)" class="text-red-500 px-4 py-2 rounded bg-red-200">Delete</button>
            </td>
          </tr>
        </table>
      </div>
    </div>
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
     methods:{
       async deleteRestuarant(id)
        {
            let result=await axios.delete('http://localhost:3000/restuarant/'+id);
            console.warn(result)
            if(result.status==200){
                this.loadData()
            }
        },
        async loadData(){
            let user = localStorage.getItem('user-info');
        this.name=JSON.parse(user).name;
        if (!user) {
            this.$router.push({ name: 'SignUp' })
        }
        let result=await axios.get('http://localhost:3000/restuarant');
        console.warn(result)
        this.restuarant=result.data;
        }
     },
    async mounted() {
        
        this.loadData()
    }
 }
 </script>

