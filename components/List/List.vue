<template>
  <ul class="list row">
    <slot/>
  </ul>
</template>

<script>
export default {
  name: "List",
  props: {},
}
</script>

<style>
.list__item img {
  max-width: 100%;
}
</style>
