<template>

<router-view/>
</template>

<script>



export default {
  name: 'App',
 
}
</script>

<style>
body{
  padding: 0;
  margin:0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  
}
.logo {
  width: 100px;
}

.register input ,.login input,.add input{
  width: 300px;
  height: 40px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid limegreen;
}

.register button , .login button , .add button{
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background-color: rgb(45, 45, 246);
  color: white;
}
</style>
