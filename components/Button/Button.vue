<template>
  <button
    @click="$emit('click')"
    class="button"
    :disabled="disabled"
    :class="[className, {'button--icon': icon, colorClassName: color}]"
    :aria-label="label"
  >
    <slot></slot>
  </button>
</template>

<script>
import Button from "@/interfaces/Button";

export default {
  name: "Button",
  props: {
    disabled: {
      type: Boolean,
      default: false
    },
    className: {
      type: String | Array,
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    icon: {
      type: Boolean,
      default: false
    },
    color: {
      type: String,
      default: '',
      validator(value) {
        return Button.colors[value] !== undefined;
      }
    }
  },
  emits: ['click'],
  computed: {
    colorClassName() {
      return `button--${this.color}`;
    }
  }
}
</script>
