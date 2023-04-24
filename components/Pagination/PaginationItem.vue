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

<style>
  .pagination__button {
    min-width: 35px;
    height: 35px;
    border: 1px solid #1B1917;
    background-color: #fff;
    font-size: 18px;

    display: flex;
    align-items: center;
    justify-content: center;

    transition-property: background-color, color;
    transition-timing-function: ease, ease;
    transition-duration: .5s, .5s;
  }

  .pagination__button:not(:disabled) {
    cursor: pointer;
  }

  .pagination__button:not(:disabled):hover, .pagination__button--active {
    background-color: #69735C;
    color: #fff;
  }
</style>
