<template>
  <svg xmlns="http://www.w3.org/2000/svg"
       :width="width"
       :height="height"
       viewBox="0 0 24 24"
       :aria-labelledby="name"
       role="presentation"
  >
    <g :fill="iconColor">
      <slot/>
    </g>
  </svg>
</template>

<script>
// TODO: Реализовать компоненту (Оля)

export default {
  name: "Icon",
  props: {
    name: {
      type: String,
      default: 'box'
    },
    width: {
      type: [Number, String],
      default: 24
    },
    height: {
      type: [Number, String],
      default: 24
    },
    iconColor: {
      type: String,
      default: 'currentColor'
    }
  },
  data() {
    return {}
  },
  computed: {},
  methods: {},
  created() {
  },
  mounted() {
  }
}
</script>
