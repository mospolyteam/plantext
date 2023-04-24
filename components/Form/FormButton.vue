<template>
  <button
    @click="$emit('click')"
    class="button form__button"
    :class="className"
    :disabled="disabled"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "FormButton",
  emits: ['click'],
  props: {
    disabled: {
      type: Boolean,
      default: false
    },
    className: {
      type: String,
      default: ''
    }
  }
}
</script>
