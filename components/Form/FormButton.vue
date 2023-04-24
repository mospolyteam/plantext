<template>
  <button
    @click="$emit('click')"
    class="button form__button"
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
    }
  }
}
</script>
