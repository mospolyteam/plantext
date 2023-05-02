<template>
  <div class="book">
    <NuxtLink :to="link">
      <img :src="book.preview" :alt="book.alt" class="book__preview">
    </NuxtLink>
    <div class="book__header">
      <h3 class="book__title">
        <NuxtLink :to="link" :aria-label="book.title">{{ book.title }}</NuxtLink>
      </h3>
      <p class="book__author">{{ book.author }}</p>
    </div>
    <div class="book__footer">
      <div class="book__rating">
        <span class="book__value">{{ book.rating }}</span>
        <Icon name="star">
          <IconStar/>
        </Icon>
      </div>
      <Button v-if="book.favorite" color="green">В избранном</Button>
      <Button v-else>В избранное</Button>
    </div>
  </div>
</template>

<script>
import IconStar from "@/components/Icon/IconStar";
import Icon from "@/components/Icon/Icon";
import Button from "@/components/Button/Button";

export default {
  name: "Book",
  components: {Button, Icon, IconStar},
  props: {
    book: {
      id: Number,
      preview: String,
      title: String,
      author: String,
      rating: Number,
      favorite: Boolean
    }
  },
  data() {
    return {

    }
  },
  computed: {
    link() {
      return '/books/' + this.book.id
    }
  },
  methods: {},
  created() {
  },
  mounted() {
  }
}
</script>

<style>
  .book {
    display: flex;
    flex-direction: column;
    gap: 10px;
    height: 100%;
  }

  .book__preview {
    width: 100%;
    height: 260px;
    object-fit: cover;
  }

  .book__title {
    font-family: 'Spectral', serif;
    font-weight: 600;
    font-size: 20px;
    margin-bottom: 5px;

    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }

  .book__rating {
    margin-bottom: 10px;
    display: flex;
    align-items: flex-start;
    gap: 5px;
    font-size: 24px;
  }

  .book__footer {
    margin-top: auto;
  }
</style>
