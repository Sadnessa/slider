<template>
  <Card><Carousel :images="images"></Carousel></Card>
</template>

<script>
import Card from './components/Card.vue'
import Carousel from './components/Carousel.vue'

export default {
  name: 'App',
  components: {
    Card,
    Carousel
  },

  data() {
    return {
     images: [
       "https://i.pinimg.com/564x/6b/82/80/6b828049f5942cd00702a9fd836fb627.jpg",
       "https://i.pinimg.com/564x/58/d1/e5/58d1e566ad7f1f5034df12dc4719dd61.jpg",
       "https://i.pinimg.com/736x/7a/80/53/7a80534a7ee888b537d7a29486770d1b.jpg",
     ],
    }
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
