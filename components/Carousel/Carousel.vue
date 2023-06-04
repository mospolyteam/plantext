<template>
  <div class="carousel">
    <button class="carousel__navigation carousel__navigation--left"
      :disabled="!canPrevious"
      @click="previous"
    >
      <img src="/previous-slide.svg">
    </button>
    <div class="carousel__wrapper">
      <div :style="variables" :class="`carousel__items row row-cols-${size}`">
        <a href="#" class="carousel__item col" v-for="(item, index) in items" :key="index">
          <img class="carousel__img" :src="item.cover" />
          <p class="carousel__title">{{ item.title }}</p>
        </a>
      </div>
    </div>
    <button class="carousel__navigation carousel__navigation--right"
      :disabled="!canNext"
      @click="next"
    >
      <img src="/next-slide.svg">
    </button>
  </div>
</template>

<script>
export default {
  name: "Carousel",
  components: {},
  data() {
    return {
      left: 0
    }
  },
  props: {
    items: {
      type: Array,
      required: true
    },
    size: {
      type: Number,
      default: 3,
    }
  },
  methods: {
    previous() {
      if (this.canPrevious) {
        this.left += 100 / this.size
      } 
    },
    next() {
      if (this.canNext) {
        this.left -= 100 / this.size
      } 
    }
  },
  computed: {
    canPrevious() {
      return this.left + 100 / this.size + 5 <= this.items.length * 100 / this.size - 100 ? true : false
    },
    canNext() {
      return this.left + 100 / this.size + 5 >= this.items.length * 100 / this.size - 100 ? true : false
    },
    variables() {
      return {
        '--left': this.left + '%'
      }
    }
  }
}
</script>
<style>
  .carousel {
    position: relative;
  }
  .carousel__items {
    position: relative;
    transition: left 0.5s;
    left: var(--left);
    flex-wrap: nowrap;
  }
  .carousel__wrapper {
    overflow: hidden;
  }
  .carousel__item {
    display: flex;
    flex-direction: column;
  }
  .carousel__img {
    height: 300px;
    width: 100%;
    object-fit: cover;
  }
  .carousel__title {
    margin-top: 15px;
    color: black;
    font-size: 18px;
  }
  .carousel__navigation {
    z-index: 1;
    position: absolute;
    width: 32px;
    height: 32px;
    background: #D95E32;
    cursor: pointer;
    top: 50%;
    transform: translateY(-50%);
  }
  .carousel__navigation--left {
    right: calc(20px + 100%);
  }
  .carousel__navigation--right {
    left: calc(20px + 100%);
  }
</style>
