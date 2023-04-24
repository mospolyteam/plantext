<template>
  <label
    :for="name"
    class="form__label"
  >
    <slot></slot>
  </label>
</template>

<script>
export default {
  name: "FormLabel",
  props: {
    name: {
      type: String,
      default: ''
    }
  }
}
</script>
