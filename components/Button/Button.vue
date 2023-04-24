<template>
  <button
    @click="$emit('click')"
    class="button"
    :disabled="disabled"
    :class="[{'button--icon': icon}, colorClassName]"
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
      default: 'red',
      validator(value) {
        return Object.values(Button.colors).includes(value);
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

<style>
  .button {
    background-color: #D95E32;
    padding: 5px 35px;
    color: #F2F1E9;
    font-size: 18px;
  }

  .button:disabled {
    opacity: .7;
  }

  .button:not(:disabled) {
    cursor: pointer;
  }

  .button--green {
    background-color: #69735C;
  }

  .button--purple {
    background-color: #A569BF;
  }
</style>
