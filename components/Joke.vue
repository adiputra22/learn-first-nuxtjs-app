<template>
    <div>
        <nuxt-link :to="'jokes/' + id">
            <div class="joke">
                <p>
                    {{ joke }}
                </p>
            </div>    
        </nuxt-link>
    </div>
</template>

<script>
export default {
    name: 'Joke',
    props: ['joke', 'id']
}
</script>

<style scoped>
.joke {
    padding: 1rem;
    border: 1px dotted #ccc;
    margin: 1rem 0;
}
</style>