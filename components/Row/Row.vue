<template>
  <div class="row" :class="classes">
    <slot/>
  </div>
</template>

<script>
export default {
  name: "Row",
  props: {
    cols: {
      type: Number,
      default: null
    }
  },
  computed: {
    classes() {
      return {
        ['row-cols-' + this.cols]: Boolean(this.cols)
      }
    }
  }
}
</script>
