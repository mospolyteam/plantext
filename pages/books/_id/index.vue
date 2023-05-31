<template>
  <main>
    <Section>
      <Breadcrumbs />
    </Section>
    <Section class="book">
      <div class="book__header">
        <h1 class="book__name">Великий Гэтсби</h1>
        <h2 class="book__author">Фрэнсис Скотт Фицджеральд</h2>
        <nav class="book__nav">
          <Navigation class="nav__menu" :items="menu" :separate="true" :gap="40" />
        </nav>
      </div>
    </Section>
  </main>
</template>

<script>
import Breadcrumbs from "~/components/Breadcrumbs/Breadcrumbs.vue";
import Section from "~/components/Section/Section.vue";
import Navigation from "~/components/Navigation/Navigation.vue";

export default {
    name: "index",
    components: {
      Breadcrumbs, Section, Navigation
    },
    props: {},
    data() {
      return {
        menu: [
          {
            text: 'Описание',
            link: '#description'
          },
          {
            text: 'Где купить',
            link: '#shops'
          },
          {
            text: 'Отзывы',
            link: '#reviews'
          },
          {
            text: 'Подборки',
            link: '#compilation'
          },
        ]
      }
    },
    computed: {},
    methods: {},
    created() {},
    mounted() {}
}
</script>

<style>
  .book__header {
    height: 193px;
    padding-left: 25%;
    gap: 20px;
    background: linear-gradient(#d95e32b7, #deb09a39);
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .book__name {
    margin: 0;
    text-align: left;
  }
  .book__nav {
    justify-content: start;
  }
  .nav__item {

  }
</style>