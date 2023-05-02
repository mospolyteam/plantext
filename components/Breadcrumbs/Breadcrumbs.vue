<template>
  <div class="breadcrumbs">
    <ul class="breadcrumbs__list">
      <BreadcrumbsItem
        v-for="(item, i) in items"
        :key="i"
        :link="item.link"
      >
        {{ item.text }}
      </BreadcrumbsItem>
    </ul>
  </div>
</template>

<script>
import BreadcrumbsItem from "~/components/Breadcrumbs/BreadcrumbsItem.vue";

const routesDictionary = {
  'books': 'Книги',
  'discussions': 'Обсуждения',
  'articles': 'Статьи'
}
export default {
  name: "Breadcrumbs",
  components: {BreadcrumbsItem},
  props: {},
  data() {
    return {}
  },
  computed: {
    items() {
      let routes = [
        {
          link: '/',
          text: 'Главная'
        }
      ];

      return this.$route.path.split('/').reduce((accum, current, index) => {
        return [...accum, this.createRouteElement(accum[index].link + current + '/', current)];
      }, routes);
    }
  },
  methods: {
    createRouteElement(link, current) {
      // TODO: Сделать обработку случаев, когда текущий путь - это цифра. Необходимо достать название статьи/книги
      // Есть две идеи. Или брать название в отдельный props, или вытаскивать из API каждый раз.
      return {
        link: link,
        text: routesDictionary[current]
      }
    }
  },
  mounted() {
  }
}
</script>
