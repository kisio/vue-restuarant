<template>
    
    <img class="logo" src="../assets/logo1.jpeg" alt="" />
    <h1>Login Page</h1>
    <div class="login">
      
        <input type="text" v-model="email" placeholder="Enter email" />
        <input type="password" v-model="password" placeholder="Enter password" />
        <p></p>
        <button >Signup</button>
        <p>
            <router-link to="/sign-up">Sign Up</router-link>
        </p>
    </div>
</template>

<script>

export default{
    name:'LoginPage'
}

</script>