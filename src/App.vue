<template>
  <Card><Carousel></Carousel></Card>
</template>

<script>
import Card from './components/Card.vue'
import Carousel from './components/Carousel.vue'

export default {
  name: 'App',
  components: {
    Card,
    Carousel
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
   width: 70%;
   height: 100%;
}

body {
   width: 100%;
   height: 100vh;
  margin: 0px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgb(218, 217, 217);
}
</style>
