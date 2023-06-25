<template>
  <ul :class="`menu ${separated}`" :style="variables">
    <NavigationItem
      v-for="(item, i) in items"
      class=""
      :key="i"
      :external="item.external"
      :link="item.link"
    >
      {{ item.text }}
    </NavigationItem>
  </ul>
</template>

<script>
import NavigationItem from "~/components/Navigation/NavigationItem.vue";

export default {
  name: "Navigation",
  components: {NavigationItem},
    props: {
      gap: {
        type: [Number, String],
        default: 30
      },
      column: {
        type: Boolean,
        default: false
      },
      items: {
        type: Array,
        default: () => []
      },
      separate: {
        type: Boolean,
        default: false
      }
    },
    computed: {
      separated: function () {
        return this.separate === true ? 'menu--separated' : ''
      },
      variables() {
        return {
          '--gap': this.gap + 'px',
          '--direction': this.column ? 'column' : 'row',
        }
      }
    }
}
</script>
<style>
  .menu {
    display: flex;
    gap: var(--gap);
    flex-direction: var(--direction);
  }
  .menu--separated {
    gap: 0;
  }
  .menu--separated > li {
    border-right: 1px solid black;
    padding: 0 calc(var(--gap) / 2);
  }
  .menu--separated > li:nth-child(1) {
    border-left: 1px solid black;
  }
</style>
