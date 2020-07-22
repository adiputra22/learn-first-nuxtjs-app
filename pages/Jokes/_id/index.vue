<template>
    <div>
        <nuxt-link to="/jokes">Back To Jokes List</nuxt-link>
        <p>{{ joke }}</p>
    </div>
</template>

<script>
import axios from "axios";

export default {
    validate ({ params, query, store }) {
        console.log(params);
        console.log(query);
        console.log(store);
        // Must be a number
        return !(/^\d+$/.test(params.id));
    },
    data() {
        return {
            joke: {}
        }
    },
    async created() {
        const config = {
            headers: {
                'Accept': 'application/json'
            }
        }

        try {
            const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
            
            console.log(res.data);

            this.joke = res.data.joke;
        } catch (err) {
            console.log(err)
        }
    },
    head() {
        return {
            title: 'Dad jokes',
            meta: [
                {
                    hid: 'description',
                    name: 'description',
                    content: 'index welcome'
                }
            ]
        }
    }
}
</script>

<style scoped>

</style>