<template>
  <div class="review">
    <div class="review__header">
      <img class="review__avatar" :src="review.user.cover" alt="Аватарка пользователя, оставившего отзыв">
      <div class="review__user">
        <a href="#" class="review__user-name">{{ review.user.name }}</a>
        <p class="review__user-age">На Plantext 4 года</p>
      </div>
    </div>
    <p class="review__text">{{ review.text }}</p>
  </div>
</template>

<script>
export default {
  name: "Review",
  components: {},
  props: {
    review: {
      type: Object,
      required: true,
    }
  },
  computed: {}
}
</script>
<style>
  .review {
    padding-bottom: 18px;
  }
  .review__header {
    display: flex;
    gap: 20px;
  }
  .review__user {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .review__user-name {
    font-size: 20px;
    font-weight: bold;
    cursor: pointer;
  }
  .review__text {
    margin-top: 10px;
  }
</style>
