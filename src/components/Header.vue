<template>
    <div class="nav">
        <router-link to="/">Home</router-link> 
        <router-link to="/Add">Add</router-link> 
        <a href="" @click="logout">logout</a>

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