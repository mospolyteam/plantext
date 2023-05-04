<template>
  <li class="header__function">
    <button class="header__button" @click="$emit('click')">
      <slot/>
    </button>
  </li>
</template>

<script>
export default {
  name: "HeaderFunction",
  emits: ['click']
}
</script>
