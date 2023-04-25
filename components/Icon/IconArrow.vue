<template>
  <path d="M18.258 10.49952H0V13.49952H18.258L10.212 21.54555L12.333 23.66655L24 11.99952L12.333 0.33252L10.212 2.45352L18.258 10.49952Z"
        :fill="fill"/>
</template>

<script>
export default {
  name: "IconArrow",
  props: {
    color: {
      type: String,
      default: 'currentColor'
    }
  },
  computed: {
    fill() {
      return this.color ? this.color : 'currentColor'
    }
  }
}
</script>
