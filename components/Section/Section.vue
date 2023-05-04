<template>
  <section class="section">
    <div class="container">
      <Row>
        <h2 v-if="title" class="section__title">{{ title }}</h2>
      </Row>
      <slot/>
    </div>
  </section>
</template>

<script>
import Row from "~/components/Row/Row.vue";
export default {
  name: "Section",
  components: {
    Row
  },
  props: {
    title: {
      type: String,
      default: null
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
