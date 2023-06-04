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
            <Rating :rating="3.5" :full="true"/>
            <div class="book-page__statistics statistics">
              <Statistic :count="2000" :type="review"/>
              <Statistic :count="2000" :type="read"/>
              <Statistic :count="20" :type="compilation"/>
            </div>
            <h3 class="book-page__title">Описание</h3>
            <p class="book-page__text">
                        Sed ut perspiciatis unde omnis iste natus error sit voluptatem 
              accusantium doloremque laudantium, totam rem aperiam, eaque ipsa 
              quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt 
              explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut 
              odit aut fugit, sed quia consequuntur magni dolores eos qui ratione 
              voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum 
              quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam 
              eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat 
              voluptatem. 
            </p>
            <h3 class="book-page__title">Где купить</h3>
            <div class="book-page__shops shops">
              <a href="#" class="shops__shop shop">Купить на ЛитРес</a>
              <a href="#" class="shops__shop shop">Купить в ЧитайГород</a>
            </div>
            <h3 class="book-page__title">Отзывы</h3>
            <div class="book-page__reviews">
              <Review 
                v-for="(review, index) in reviews" 
                :key="index" 
                :review="review" 
                class="book-page__review"  
              />
            </div>
            <h3 class="book-page__title">Подборки</h3>
            <Carousel :items="compilations" />
          </div>
          <div class="book-page__shops shops">
            <a href="#" class="shops__shop shop">Купить на ЛитРес</a>
            <a href="#" class="shops__shop shop">Купить в ЧитайГород</a>
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
import Rating from "~/components/Rating/Rating.vue";
import Review from "~/components/Review/Review.vue";
import Carousel from "~/components/Carousel/Carousel.vue";
import Statistic from "~/components/Statistic/Statistic.vue";
import StatisticTypes from "~/interfaces/Statistic.ts";
import IconStar from "~/components/Icon/IconStar.vue";
import IconHeart from "~/components/Icon/IconHeart.vue";
import IconQuote from "~/components/Icon/IconQuote.vue";
import IconReview from "~/components/Icon/IconReview.vue";

export default {
    name: "index",
    components: {
      Breadcrumbs, Section, Navigation, Rating, Review, Carousel, Statistic, IconStar, IconHeart, IconQuote, IconReview
    },
    props: {},
    data() {
      return {
        review: StatisticTypes.REVIEW,
        read: StatisticTypes.READ,
        compilation: StatisticTypes.COMPILATION,
        compilations: [
          {
            cover: "/images/book.jpg",
            title: "Американская классикаdddd",
          },
          {
            cover: "/images/book1.jpg",
            title: "Американская классика",
          },
          {
            cover: "/images/book.jpg",
            title: "Американская классика",
          },
          {
            cover: "/images/book1.jpg",
            title: "Американская классика",
          },
        ],
        reviews: [
          {
            user: {
              name: "Анна",
              cover: "/images/anna.png"
            },
            text: `Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore 
            magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco Lorem ipsum dolor sit amet, consectetur 
            adipiscing elit, sed do eiusmod tempor incididunt`
          },
          {
            user: {
              name: "Анна",
              cover: "/images/anna.png"
            },
            text: `Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore 
            magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco Lorem ipsum dolor sit amet, consectetur 
            adipiscing elit, sed do eiusmod tempor incididunt`
          },
        ],
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
    margin-top: 20px;
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
  .book-page__info {
    padding: 22.5px 0;
  }
  .book-page__title {
    margin: 25px 0;
  }
  .book-page__text {
    margin-bottom: 15px;
  }
  .statistics {
    display: flex;
    gap: 65.5px;
    margin-top: 19px;
  }
  .shops {
    display: flex;
    flex-direction: column;
    gap: 5px;
    margin-bottom: 15px;
  }
  .shops__shop {
    width: max-content;
    text-decoration: underline;
  }
  .shops__shop:hover {
    text-decoration: none;
  }
  .book-page__review:not(:nth-last-child(1)) {
    border-bottom: 1px solid #000;
    margin-bottom: 12.5px;
  }
</style>