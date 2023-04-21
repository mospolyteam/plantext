<template>
  <li class="pagination__item">
    <button
      @click.prevent="$emit('click')"
      :disabled="disabled"
      class="pagination__button"
      :class="{'pagination__button--active': active}"
    >
      <slot></slot>
    </button>
  </li>
</template>

<script>
export default {
  name: "PaginationItem",
  props: {
    active: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    }
  }
}
</script>
