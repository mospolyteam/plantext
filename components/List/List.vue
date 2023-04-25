<template>
  <ul
    class="list"
    :style="styles"
  >
    <slot></slot>
  </ul>
</template>

<script>
export default {
  name: "List",
  props: {
    gap: {
      type: Number,
      default: 0
    },
    size: {
      type: Number,
      default: 3
    },
    column: {
      type: Boolean,
      default: false
    },
    reverse: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {}
  },
  computed: {
    styles() {
      return {
        '--gap': this.gap + 'px',
        '--item-width': 'calc(' + (100 / this.size) + '% - ' + (this.gap - this.gap / this.size) + 'px)',
        '--direction': (this.column ? 'column' : 'row') + (this.reverse ? '-reverse' : '')
      }
    }
  }
}
</script>

<style>
  .list {
    display: flex;
    justify-content: flex-start;
    flex-direction: var(--direction);
    gap: var(--gap);
  }

  .list__item {
    width: var(--item-width);
  }

  .list__item img {
    max-width: 100%;
  }
</style>
