
<template>
    <div class="nav bg-blue-500 text-white py-4">
      <router-link class="mr-4" to="/">Home</router-link>
      <router-link class="mr-4" to="/Add">Add</router-link>
      <a class="mr-4" href="#" @click="logout">Logout</a>
    </div>
  </template>
  
<script>
export default{
    name:'HeaderS',
    methods:{
        logout(){
            localStorage.clear();
            this.$router.push('/Login');
        }
    }
}
</script>


<style>
.nav{
    background-color: rgb(130, 83, 212);
    overflow:hidden;
    color:white;

}
.nav a{
    float: left;
    color:white;
    padding: 14px;
    text-align: center;
    text-decoration: none;
    font-size: 20px;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
    
}
a:hover{
    color: rgb(126, 218, 227);
}
</style>