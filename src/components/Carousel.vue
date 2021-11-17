<template>
  <div class="carousel">
    <div class="carousel__button carousel__button--left" @click="prev">
      <span class="material-icons"> chevron_left </span>
    </div>
    <div class="carousel__button carousel__button--right" @click="next">
      <span class="material-icons"> chevron_right </span>
    </div>
    <div class="indicators">
      <div
        class="carousel__button carousel__button--small"
        v-for="i in images.length"
        :key="i"
        :class="{ 'carousel__button--active': i - 1 == currentSlide }"
        @click="indicator(i - 1)"
      ></div>
    </div>
    <div class="carousel__content" :style="{ 'margin-left': margin }">
      <div class="slideimg" v-for="image in images" :key="image">
        <img :src="image" />
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

  mounted() {
    this.myIntr = setInterval(() => { 
      if (this.currentSlide === this.images.length - 1) {
        this.currentSlide = 0;
        return
      }
      this.currentSlide += 1;
    }, 2000);
  },

  beforeUnmount() {
    clearInterval(this.myIntr);
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
        this.currentSlide = 0;
        return;
      }
      this.currentSlide += 1;
    },

    prev() {
      if (this.currentSlide === 0) {
        this.currentSlide = this.images.length - 1;
        return;
      }
      this.currentSlide -= 1;
    },

    indicator(i) {
      this.currentSlide = i;
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

  .indicators {
    width: 100%;
    position: absolute;
    bottom: 10px;
    display: flex;
    justify-content: center;

    & > * {
      margin: 0 5px;
    }
  }

  &__button {
    background-color: rgba(37, 37, 37, 0.5);
    border-radius: 50%;
    height: 30px;
    width: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    cursor: pointer;
    user-select: none;
    transition: all 0.2s ease-in-out;

    &:hover {
      background: rgba(100, 100, 100, 0.5);
      color: rgb(77, 77, 77);
    }

    &--active {
      background: rgba(53, 53, 53, 0.5);
      border: 3px solid;
      border-color: rgba(255, 255, 255, 0.5);
      box-sizing: border-box;
    }

    &--right {
      right: 15px;
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
    }

    &--left {
      left: 15px;
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
    }

    &--small {
      height: 15px;
      width: 15px;
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