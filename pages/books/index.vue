<template>
  <main>
    <Section class="books" title="Популярные книги">
      <List :gap="20" :size="6">
        <ListItem v-for="book in books" :key="book.id">
          <Book :book="book"/>
        </ListItem>
      </List>
    </Section>
  </main>
</template>

<script>

import Section from "~/components/Section/Section.vue";
import List from "~/components/List/List.vue";
import ListItem from "~/components/List/ListItem.vue";
import Book from "~/components/Book/Book.vue";

export default {
    name: "index.vue",
    components: {
      Section, List, ListItem, Book
    },
    props: {},
    data() {
        return {
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
        }
    },
    computed: {},
    methods: {},
    created() {},
    mounted() {}
}
</script>
