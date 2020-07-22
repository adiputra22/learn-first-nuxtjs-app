<template>
  <div>
    <SearchJokes v-on:search-text="searchText" />
    <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke" />
  </div>
</template>

<script>
import axios from "axios";
import Joke from "@/components/Joke";
import SearchJokes from "@/components/SearchJokes";

export default {
  components: {
    Joke,
    SearchJokes
  },
  data() {
    return {
      jokes: []
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          'Accept': 'application/json'
        }
      }

      try {
        const res = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
        
        console.log(res.data);

        this.jokes = res.data.results;
      } catch (err) {
        console.log(err)
      }
    }
  },
  async created() {
    const config = {
      headers: {
        'Accept': 'application/json'
      }
    }

    try {
      const res = await axios.get('https://icanhazdadjoke.com/search', config);
      
      console.log(res.data);

      this.jokes = res.data.results;
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
