<template>
  <main>
    <section class="hero">
      <Slider></Slider>
    </section>
    <Section class="about" title="О нашем форуме">
      <div class="about__content">
        <div class="about__text">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et
            dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex
            ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat
            nulla pariatur.</p>
        </div>
        <img src="/images/hello.png" alt="hello" class="about__image">
      </div>
    </Section>
    <Section class="articles" title="Актуальные статьи">
      <List :gap="20">
        <ListItem v-for="article in articles" :key="article.id">
          <Article :article="article"/>
        </ListItem>
      </List>
    </Section>
    <Section class="books" title="Популярные книги">
      <List :gap="20" :size="6">
        <ListItem v-for="book in books" :key="book.id">
          <Book :book="book"/>
        </ListItem>
      </List>
    </Section>
    <Section class="discussions" title="Горячие обсуждения">
      <List :gap="20" :size="2">
        <ListItem v-for="discussion in discussions" :key="discussion.id">
          <Discussion :discussion="discussion"/>
        </ListItem>
      </List>
    </Section>
    <Section class="follow" title="Станьте частью сообщества">
      <div class="follow__content">
        <p class="follow__text"> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
          incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco
          laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit
          esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui
          officia deserunt mollit anim id est laborum.</p>
        <Button class="follow__button" color="purple" big>Стать нашим писателем</Button>
      </div>
    </Section>
    <Section class="partners" title="Партнёры">
      <List :gap="35" :size="4">
        <ListItem v-for="partner in partners" :key="partner.id">
          <Partner :partner="partner" />
        </ListItem>
      </List>
    </Section>
  </main>
</template>

<script lang="ts">
import Pagination from "~/components/Pagination/Pagination.vue";
import Button from "~/components/Button/Button.vue";
import FormField from "~/components/Form/FormField.vue";
import FormSelect from "~/components/Form/FormSelect.vue";
import Slider from "~/components/Slider/Slider.vue";
import Section from "~/components/Section/Section.vue";
import Article from "~/components/Article/Article.vue";
import List from "~/components/List/List.vue";
import ListItem from "~/components/List/ListItem.vue";
import Book from "~/components/Book/Book.vue";
import Discussion from "~/components/Discussion/Discussion.vue";
import Partner from "~/components/Partner/Partner.vue";

export default {
  name: 'IndexPage',
  components: {
    Partner,
    Discussion, Book, ListItem, Article, Section, Slider, FormSelect, FormField, Button, Pagination, List},
  data() {
    return {
      articles: [
        {
          id: 1,
          title: 'Образы природы в литературе',
          preview: '/images/article-1.png'
        },
        {
          id: 2,
          title: 'Образы природы в литературе',
          preview: '/images/article-1.png'
        },
        {
          id: 3,
          title: 'Образы природы в литературе',
          preview: '/images/article-1.png'
        }
      ],
      books: [
        {
          id: 1,
          preview: '/images/book.jpg',
          title: 'Испанская книга',
          author: 'Люси Эрадо',
          rating: 5.0,
          favorite: false
        },
        {
          id: 2,
          preview: '/images/book.jpg',
          title: 'Сдвиг. Как выжить в стремительном будущем, в котором ничего не будет',
          author: 'Люси Эрадо',
          rating: 5.0,
          favorite: true
        },
        {
          id: 3,
          preview: '/images/book.jpg',
          title: 'Испанская книга',
          author: 'Люси Эрадо',
          rating: 5.0,
          favorite: false
        },
        {
          id: 4,
          preview: '/images/book.jpg',
          title: 'Сдвиг. Как выжить в стремительном будущем, в котором ничего не будет',
          author: 'Люси Эрадо',
          rating: 5.0,
          favorite: true
        },
        {
          id: 5,
          preview: '/images/book.jpg',
          title: 'Испанская книга',
          author: 'Люси Эрадо',
          rating: 5.0,
          favorite: false
        },
        {
          id: 6,
          preview: '/images/book.jpg',
          title: 'Сдвиг. Как выжить в стремительном будущем, в котором ничего не будет',
          author: 'Люси Эрадо',
          rating: 5.0,
          favorite: true
        }
      ],
      discussions: [
        {
          id: 1,
          title: 'Стоят ли бумажные книги своих денег?'
        },
        {
          id: 2,
          title: 'Стоят ли бумажные книги своих денег?'
        }
      ],
      partners: [
        {
          id: 1,
          alt: 'litres',
          link: '#',
          image: '/images/litres.png'
        },
        {
          id: 2,
          alt: 'chitai-gorod',
          link: '#',
          image: '/images/chitai-gorod.png'
        },
        {
          id: 3,
          alt: 'labirint',
          link: '#',
          image: '/images/labirint.png'
        },
        {
          id: 4,
          alt: 'book24',
          link: '#',
          image: '/images/book24.png'
        }
      ]
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Spectral:wght@300;400;500;600;700&family=Tenor+Sans&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Tenor Sans', sans-serif;
  background-color: #F2F1E9;
  color: #1B1917;
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
  color: inherit;
}

h2 {
  font-weight: 400;
  font-size: 32px;
}

h3 {
  font-weight: 400;
  font-size: 24px;
}

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}

.about__content {
  display: flex;
  align-items: center;
}

.about__image {
  margin: -50px 120px 0;
}

.about__text {
  text-indent: 30px
}

.follow__text {
  font-size: 18px;
  margin-bottom: 10px;
  text-indent: 30px
}

.follow__button {
  margin: 0 auto;
}
</style>
