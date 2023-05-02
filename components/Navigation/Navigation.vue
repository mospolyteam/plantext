<template>
  <ul class="menu" :style="variables">
    <NavigationItem
      v-for="(item, i) in items"
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
      }
    },
    computed: {
      variables() {
        return {
          '--gap': this.gap + 'px',
          '--direction': this.column ? 'column' : 'row'
        }
      }
    }
}
</script>
<style>
  .menu {
    display: flex;
    align-items: center;
    gap: var(--gap);
    flex-direction: var(--direction);
  }
</style>
