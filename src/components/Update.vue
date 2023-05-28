<template>
    <Header />
    <h1>Hello, welcome to the Update page</h1>
    <form class="add">
        <input type="text" mame="name" placeholder="Enter Name" v-model="restuarant.name" />
        <input type="text" mame="address" placeholder="Enter Address" v-model="restuarant.address" />
        <input type="text" mame="city" placeholder="Enter City" v-model="restuarant.city" />
        <input type="text" mame="state" placeholder="Enter State" v-model="restuarant.state" />
        <button @click="updateRestuarant()" type="button">Update Hotel</button>
    </form>
</template>
<script>
import Header from './Header.vue'
import axios from 'axios';
export default {
    name: 'UpdatePage',
    components: {
        Header
    },
    data() {
        return {
            restuarant: {
                name: '',
                address: '',
                city: '',
                state: ''
            }
        }
    },
    methods: {

        async updateRestuarant() {
            const result = await axios.put("http://localhost:3000/restuarant/" + this.$route.params.id, {
                name: this.restuarant.name,
                address: this.restuarant.address,
                city: this.restuarant.city,
                state: this.restuarant.state,
            });
            if (result.status == 200) {
                this.$router.push('/');
            }
        }

    },
    async mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({ name: 'SignUp' })
        }
        const result = await axios.get('http://localhost:3000/restuarant/' + this.$route.params.id)
        console.warn(result.data)
        this.restuarant = result.data
    }
}
</script>