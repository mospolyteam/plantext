<template>
  <div class="slider__slide slide">
    <img class="slide__cover" :src="`${cover}`">
    <slot name="title" />
    <slot name="child" />
  </div>
</template>

<script>
export default {
    name: "SliderItem",
    props: {
      cover: String,
    },
    data() {
        return {}
    },
    computed: {},
    methods: {},
    created() {},
    mounted() {}
}
</script>

<style>
  .slide {
    position: absolute;
    visibility: hidden;
    transform: scale(0.75);
  }
  .slide__cover {
    width: 100%;
    height: inherit;
    object-fit: cover;
  }
  .next {
    visibility: hidden;
    left: 100%;
    transition: left 1s, visibility 1s, transform 1s ease-in;
  }
  .previous {
    visibility: hidden;
    left: -100%;
    transition: left 1s, visibility 1s, transform 1s ease-in;
  }
  .active {
    transform: scale(1);
    visibility: visible;
    left: 0%;;
    transition: left 1s, transform 1s ease-out;
  }
  .slide__title, .slide__child {
    position: absolute;
    max-width: 40%;
    max-height: 40%;
    font-size: 36px;
    color: white;
  }
  .slide__child {
    display: flex;
  }
  .slide__form > .form__field{
    display: flex;
  }
  .slide__title--1, .slide__child--1 {
    top: 30px;
    left: 102px;
  }
  .slide__title--2, .slide__child--2 {
    top: 30px;
    right: 102px;
  }
  .slide__title--3, .slide__child--3 {
    bottom: 30px;
    left: 102px;
  }
  .slide__title--4, .slide__child--4 {
    bottom: 30px;
    right: 102px;
  }
</style>
