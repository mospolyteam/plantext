<template>
  <NuxtLink
    class="button button--link"
    :to="to"
    :class="[{'button--icon': icon, 'button--big': big}, colorClassName]"
    :aria-label="label"
  >
    <slot></slot>
  </NuxtLink>
</template>

<script>
import Button from "@/interfaces/Button";

export default {
  name: "ButtonLink",
  props: {
    to: {
      type: String,
      default: '#',
      required: true
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
        return Object.values(Button.colors).includes(value);
      }
    },
    big: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    colorClassName() {
      return `button--${this.color}`;
    }
  }
}
</script>
