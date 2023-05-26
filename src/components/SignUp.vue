<template>
    <img class="logo" src="../assets/logo1.jpeg" alt="" />
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Name" />
        <input type="text" v-model="email" placeholder="Enter email" />
        <input type="password" v-model="password" placeholder="Enter password" />
        <p></p>
        <button v-on:click="signUp()">Signup</button>
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
};
</script>

<style>
.logo {
    width: 100px;
}

.register input {
    width: 300px;
    height: 40px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border: 1px solid limegreen;
}

.register button {
    width: 320px;
    height: 40px;
    border: 1px solid skyblue;
    background-color: rgb(45, 45, 246);
    color: white;
}
</style>
