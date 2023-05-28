
<template>
    <div class="flex flex-col items-center justify-center h-screen bg-gray-100">
      <img class="w-32 h-32 mb-8 rounded-full" src="../assets/logo1.jpeg" alt="Logo" />
      <h1 class="text-3xl font-bold mb-4">Sign Up</h1>
      <div class="bg-white rounded-lg shadow-md p-6">
        <input type="text" v-model="name" placeholder="Enter Name" class="border border-gray-300 rounded-md px-4 py-2 mb-4 focus:outline-none focus:border-blue-500 w-64" />
        <input type="text" v-model="email" placeholder="Enter email" class="border border-gray-300 rounded-md px-4 py-2 mb-4 focus:outline-none focus:border-blue-500 w-64" />
        <input type="password" v-model="password" placeholder="Enter password" class="border border-gray-300 rounded-md px-4 py-2 mb-4 focus:outline-none focus:border-blue-500 w-64" />
        <button v-on:click="signUp" class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded w-64">Sign Up</button>
        <p class="mt-4">
          <router-link to="/login" class="text-blue-500 hover:underline">Login</router-link>
        </p>
      </div>
    </div>
  </template>
  
  
<script>
import axios from "axios";
export default {
    name: "SignUp",
    data() {
        return {
            name: "",
            email: "",
            password: "",
        };
    },
    methods: {
        async signUp() {
            let result = await axios.post("http://localhost:3000/users", {
                email: this.email,
                password: this.password,
                name: this.name,
            });

            console.warn(result);
            if (result.status == 201) {

                localStorage.setItem("user-info", JSON.stringify(result.data));
                this.$router.push({ name: 'Home' })
            }
        },
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if (user) {
            this.$router.push({ name: 'Home' })
        }
    }
};
</script>

<style>

</style>
