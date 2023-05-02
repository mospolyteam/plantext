<template>
  <li class="menu__item">
    <a v-if="external" :href="link">
      <slot/>
    </a>
    <NuxtLink v-else :to="link">
      <slot/>
    </NuxtLink>
  </li>
</template>

<script>
export default {
  name: "NavigationItem",
  props: {
    external: {
      type: Boolean,
      default: false
    },
    link: {
      type: String,
      default: '/'
    }
  }
}
</script>
