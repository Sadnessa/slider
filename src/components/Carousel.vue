<template>
  <div class="carousel">
    <div class="carousel__button carousel__button--left" @click="prev">L</div>
    <div class="carousel__button carousel__button--right" @click="next">R</div>
    <div class="carousel__content" :style="{ 'margin-left': margin }">
      <div class="slideimg" v-for="image in images" :key="image">
        <img :src="image"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    images: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      currentSlide: 0,
    };
  },

  computed: {
    margin() {
      return this.currentSlide * -100 + "%";
    },
  },

  methods: {
    next() {
      if (this.currentSlide === this.images.length - 1) {
        return
      }
      this.currentSlide += 1;
    },

    prev() {
      if(this.currentSlide === 0) {
        return
      }
      this.currentSlide -= 1;
    },
  },
};
</script>

<style lang="scss" scoped>
.carousel {
  width: 70%;
  height: 50%;
  background: white;
  box-shadow: -1px -1px 15px -2px rgba(34, 60, 80, 0.2);
  border-radius: 10px;
  position: relative;
  overflow: hidden;

  &__button {
    background-color: rgb(37, 37, 37);
    position: absolute;
    top: 50%;
    border-radius: 50%;
    height: 30px;
    width: 30px;
    transform: translateY(-50%);

    &--right {
      right: 15px;
    }

    &--left {
      left: 15px;
    }
  }

  &__content {
    width: 100%;
    height: 100%;
    white-space: nowrap;
    transition: all 0.3s ease-in-out;

    .slideimg {
      display: inline-flex;
      justify-content: center;
      width: 100%;
      height: 100%;
    }

    img {
      max-height: 100%;
      max-width: 100%;
      border-radius: 10px;
    }
  }
}
</style>