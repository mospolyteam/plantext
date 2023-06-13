<template>
  <div v-if="full" class="rating rating--full">
    <IconStar v-for="n in Math.round(rating)" :key="n" />
    <IconStarEmpty v-for="n in (5 - Math.round(rating))" :key="5 - n"/>
    <span class="rating__value rating__value--full">{{ fullRating }}</span>
  </div>
  <div v-else class="rating">
    <span class="rating__value">{{ rating }}</span>
    <IconStar/>
  </div>
</template>

<script>
import IconStar from "~/components/Icon/IconStar.vue";
import IconStarEmpty from "~/components/Icon/IconStarEmpty.vue";

export default {
  name: "Rating",
  components: {
    IconStar, IconStarEmpty
    },
  props: {
    rating: {
      type: Number,
      required: true
    },
    full: {
      type: Boolean,
      default: false,
    }
  },
  computed: {
    fullRating: function() {
      return this.rating.toFixed(1)
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
  .rating--full {
    align-items: center;
  }
  .rating__value--full {
    margin-left: 15px;
  }
</style>
