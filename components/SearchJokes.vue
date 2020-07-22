<template>
    <div>
        <form @submit.prevent="onSubmit">
            <input type="text" v-model="text" placeholder="search jokes">
            <input type="submit" value="Search">
        </form>
    </div>    
</template>

<script>
export default {
    name: 'SearchJokes',
    data() {
        return {
            text: ''
        }
    },
    methods: {
        onSubmit() {
            this.$emit('search-text', this.text);
            this.text = '';
        }
    }
}
</script>

<style scoped>

</style>