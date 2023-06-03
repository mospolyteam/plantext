<template>
  <main>
    <Section>
      <Breadcrumbs />
    </Section>
    <Section class="book-page">
      <div class="book-page__wrapper">
        <div class="book-page__header">
          <h1 class="book-page__name">Великий Гэтсби</h1>
          <h2 class="book-page__author">Фрэнсис Скотт Фицджеральд</h2>
          <nav class="book-page__nav">
            <Navigation class="nav__menu" :items="menu" :separate="true" :gap="40" />
          </nav>
        </div>
        <div class="book-page__content">
          <div class="book-page__actions">
            <img src="/images/book.jpg" alt="Book cover" class="book-page__cover">
            <ul class="book-page__actions-list action-list">
              <li class="action-list__item">
                <a href="#" class="action-list__link">
                  <IconHeart />
                  Добавить в избранное
                </a>
              </li>
              <li class="action-list__item">
                <a href="#" class="action-list__link">
                  <IconQuote />
                  Добавить цитату
                </a>
              </li>
              <li class="action-list__item">
                <a href="#" class="action-list__link">
                  <IconReview />
                  Написать отзыв
                </a>
              </li>
            </ul>
          </div>
          <div class="book-page__info">
            Rating
          </div>
          <div class="book-page__shops">
            Buy
          </div>
        </div>
      </div>
    </Section>
  </main>
</template>

<script>
import Breadcrumbs from "~/components/Breadcrumbs/Breadcrumbs.vue";
import Section from "~/components/Section/Section.vue";
import Navigation from "~/components/Navigation/Navigation.vue";
import IconStar from "~/components/Icon/IconStar.vue";
import IconHeart from "~/components/Icon/IconHeart.vue";
import IconQuote from "~/components/Icon/IconQuote.vue";
import IconReview from "~/components/Icon/IconReview.vue";

export default {
    name: "index",
    components: {
      Breadcrumbs, Section, Navigation, IconStar, IconHeart, IconQuote, IconReview
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
  .book-page__wrapper {
    position: relative;
  }
  .book-page__header {
    height: 193px;
    padding-left: 305px;
    gap: 20px;
    background: linear-gradient(#d95e32b7, #deb09a39);
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .book-page__name {
    margin: 0;
    text-align: left;
  }
  .book-page__nav {
    justify-content: start;
  }
  .book-page__content {
    display: flex;
  }
  .book-page__actions {
    padding: 0 20px;
    display: flex;
    flex-direction: column;
    margin-top: -175px;
    box-sizing: border-box;
    flex: 1;
  }
  .book-page__info {
    flex: 3;
  }
  .book-page__shops {
    flex: 1;
  }
  .book-page__cover {
    width: 265px;
    cursor: pointer;
  }
  .action-list {
    margin-top: 29px;
    width: 100%;
  }
  .action-list__item:not(:nth-last-child(1)) {
    margin-bottom: 15px;
  }
</style>