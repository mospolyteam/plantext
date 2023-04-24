<template>
  <label
    :for="name"
    class="form__label"
    :class="className"
  >
    <slot></slot>
  </label>
</template>

<script>
export default {
  name: "FormLabel",
  props: {
    className: {
      type: String,
      default: ''
    },
    name: {
      type: String,
      default: ''
    }
  }
}
</script>
