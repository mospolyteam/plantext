<template>
  <div class="rating">
    <span class="rating__value">{{ rating }}</span>
    <IconStar/>
  </div>
</template>

<script>
import IconStar from "~/components/Icon/IconStar.vue";

export default {
  name: "Rating",
  components: {IconStar},
  props: {
    rating: {
      type: Number,
      required: true
    }
  }
}
</script>
<style>
  .rating {
    display: flex;
    align-items: flex-start;
    gap: 5px;
    font-size: 24px;
  }
</style>
