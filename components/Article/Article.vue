<template>
  <article class="article">
    <NuxtLink :to="link">
      <img :src="article.preview" :alt="article.alt" class="article__preview">
    </NuxtLink>
    <h3 class="article__title">
      <NuxtLink :to="link">{{ article.title }}</NuxtLink>
    </h3>
  </article>
</template>

<script>
export default {
  name: "Article",
  props: {
    article: {
      title: String,
      id: Number,
      preview: String,
      alt: String
    }
  },
  computed: {
    link() {
      return '/articles/' + this.article.id
    }
  }
}
</script>

<style>
  .article__title {
    margin-top: 10px;
    max-width: 80%;
  }

  .article__preview {
    height: 200px;
    width: 100%;
    object-fit: cover;
  }
</style>
