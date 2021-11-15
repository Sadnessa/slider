<template>
  <div class="carousel">
    <div class="carousel__button carousel__button--left" @click="prev">L</div>
    <div class="carousel__button carousel__button--right" @click="next">R</div>
    <div class="carousel__content" :style="{ 'margin-left': margin }">
      <div class="slideimg" >
        <img
          src="https://i.pinimg.com/564x/6b/82/80/6b828049f5942cd00702a9fd836fb627.jpg"
        />
      </div>
      <div class="slideimg">
        <img
          src="https://i.pinimg.com/564x/58/d1/e5/58d1e566ad7f1f5034df12dc4719dd61.jpg"
        />
      </div>
      <div class="slideimg">
        <img
          src="https://i.pinimg.com/736x/7a/80/53/7a80534a7ee888b537d7a29486770d1b.jpg"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentSlide: 0,
    };
  },

  computed: {
      margin() {
          return this.currentSlide * -100 + '%'
      }
  },

  methods: {
    next() {
        this.currentSlide += 1
    },

prev() {
        this.currentSlide -= 1
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