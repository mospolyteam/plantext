<template>
  <div class="breadcrumbs">
    <ul class="breadcrumbs__list">
      <template v-for="(item, i) in routes">
        <BreadcrumbsItem :link="item.link" :key="item.id">{{ item.text }}</BreadcrumbsItem>
        <IconRight v-if="i !== routes.length - 1" :key="item.id"/>
      </template>
    </ul>
  </div>
</template>

<script>
import BreadcrumbsItem from "~/components/Breadcrumbs/BreadcrumbsItem.vue";
import IconRight from "~/components/Icon/IconRight.vue";

const routesDictionary = {
  'books': 'Книги',
  'discussions': 'Обсуждения',
  'articles': 'Статьи'
}

export default {
  name: "Breadcrumbs",
  components: {IconRight, BreadcrumbsItem},
  props: {
    current: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      routes: [
        {
          link: '/',
          text: 'Главная'
        }
      ]
    }
  },
  computed: {},
  methods: {
    createRouteElement(link, current) {
      return {
        link: link,
        text: /^\d+$/.test(current) ? this.current : routesDictionary[current]
      }
    }
  },
  created() {
    let splitPath = this.$route.path.split('/');
    splitPath.shift();

    splitPath.map((element, index) => {
      this.routes.push(this.createRouteElement(this.routes[index].link + element + '/', element));
    });
  }
}
</script>

<style>
  .breadcrumbs__list {
    display: flex;
    align-items: center;
    gap: 6px;
  }
</style>
