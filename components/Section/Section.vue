<template>
  <section class="section">
    <div class="container">
      <div class="row">
        <h2 class="section__title">{{ title }}</h2>
        <slot></slot>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Section",
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
  .section {
    margin-bottom: 40px;
  }

  .section__title {
    margin-bottom: 25px;
  }
</style>
