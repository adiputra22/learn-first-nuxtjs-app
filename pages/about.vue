<template>
  <div>
    <h1>About Page</h1>
    <p>This is app that displays corny dad jokes</p>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: 'About the app',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'this is full name description'
        }
      ]
    }
  }
}
</script>

<style scoped>

</style>
