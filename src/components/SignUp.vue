<template>
    <img class="logo" src="../assets/logo1.jpeg" alt=""/>
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" placeholder="Enter Name"/>
        <input type="text" placeholder="Enter email"/>
        <input type="text" placeholder="Enter password"/>
        <p></p>
        <button>Signup</button>
    </div>
</template>

<script>
export default{
    name:'SignUp'
}
</script>

<style>
.logo{
    width: 100px;
}
.register input{
    width:300px;
    height:40px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid limegreen;
    

}
.register button{
    width:320px;
    height:40px;
    border:1px solid skyblue;
    background-color: rgb(45, 45, 246);
    color: white;

}
</style>