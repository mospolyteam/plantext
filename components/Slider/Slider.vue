<template>
  <div class="container">
    <div class="slider">
      <button class="slider__navigation slider__navigation--left"
        :disabled="inProcess"
        @click="previousSlide"
      >
        <img src="previous-slide.svg">
      </button>
      <slider-item
        v-for="slide in slides"
        :class="slidePosition(slide.id)"
        :key="slide.id"
        :titleColor="slide.titleColor"
        :childPosition="slide.childPosition"
        :cover="slide.cover"
      >
        <template v-slot:title>
          <p :class="`slide__title slide__title--${slide.titlePosition}`"
            :style="{color: slide.titleColor}"
          >
            {{ slide.title }}
          </p>
        </template>
        <template v-slot:child>
          <!-- Заглушка -->
          <div :class="`slide__child slide__child--${slide.childPosition}`">
            <input type="text" />
            <Button 
              label="Подписаться"
              color="purple"
            >
              Подписаться
            </Button>
          </div>
        </template>
      </slider-item>
      <button class="slider__navigation slider__navigation--right"
        :disabled="inProcess"
        @click="nextSlide"
      >
        <img src="next-slide.svg">
      </button>
    </div>
  </div>
</template>

<script>
import Button from "~/components/Button/Button.vue";

export default {
  name: "Slider",
  components: {
    Button
  },
  props: {},
  data() {
    return {
      currentSlide: 1,
      inProcess: false,
      slides: [
        {
          id: 1,
          title: "Подпишитесь на нашу рассылку",
          titleColor: "#F2F1E9",
          titlePosition: 1,
          childPosition: 4,
          cover: "/images/slide-mail.jpg",
        },
        {
          id: 2,
          title: "Подпишитесь на нашу рассылку",
          titleColor: "#F2F1E9",
          titlePosition: 2,
          childPosition: 3,
          cover: "/images/slide-mail.jpg",
        },
        {
          id: 3,
          title: "Подпишитесь на нашу рассылку",
          titleColor: "#F2F1E9",
          titlePosition: 3,
          childPosition: 1,
          cover: "/images/slide-mail.jpg",
        },
        {
          id: 4,
          title: "Подпишитесь на нашу рассылку",
          titleColor: "#F2F1E9",
          titlePosition: 4,
          childPosition: 2,
          cover: "/images/slide-mail.jpg"
        }
      ]
    }
  },
  watch: {
    currentSlide() {
      if (this.currentSlide > this.slides.length) {
        this.currentSlide = 1
      }
      if (this.currentSlide <= 0) {
        this.currentSlide = this.slides.length
      }
    }
  },
  computed: {
    },
  methods: {
    slidePosition(id) {
      if (id === this.currentSlide) {
        return 'active'
      } else if (
        (id === this.currentSlide + 1) || 
        ((this.currentSlide === this.slides.length) && (id === 1))
      ) {
        return 'next'
      } else if (
        (id === this.currentSlide - 1) || 
        ((this.currentSlide === 1) && (id === this.slides.length))
      ) {
        return 'previous'
      }
      return ''
    },
    nextSlide() {
      this.setInProcess()
      this.currentSlide++
    },
    previousSlide() {
      this.setInProcess()
      this.currentSlide--
    },
    setInProcess() {
      this.inProcess = true
      setTimeout(() => {
        this.inProcess = false
      }, 1000)
    },
  },
  created() {},
  mounted() {}
}
</script>

<style>
  .slider {
    position: relative;
    height: 330px;
    overflow: hidden;
  }
  .slider__navigation {
    z-index: 1;
    position: absolute;
    width: 32px;
    height: 32px;
    background: #D95E32;
    cursor: pointer;
    top: 50%;
    transform: translateY(-50%);
  }
  .slider__navigation--left {
    left: 20px;
  }
  .slider__navigation--right {
    right: 20px;
  }
</style>
