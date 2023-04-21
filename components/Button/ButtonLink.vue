<template>
  <NuxtLink
    class="button button--link"
    :to="to"
    :class="[className, {'button--icon': icon, colorClassName: color}]"
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
  computed: {
    colorClassName() {
      return `button--${this.color}`;
    }
  }
}
</script>
