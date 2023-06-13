<template>
  <div class="statistic">
    <span class="statistic__value">{{ count }}</span>
    <span class="statistic__type">{{ type }}</span>
  </div>
</template>

<script>
export default {
    name: "Statistic",
    props: {
      count: {
        type: Number,
        required: true
      },
      type: {
        type: String,
        required: true
      }
    },
    data() {
        return {}
    },
    computed: {
    },
}
</script>

<style>
  .statistic {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: min-content;
  }
  .statistic__value {
    font-size: 24px;
  }
</style>
