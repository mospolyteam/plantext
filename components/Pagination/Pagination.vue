<template>
  <div class="pagination">
    <ul class="pagination__list">
      <PaginationItem
        @click="updatePage(1)"
        :disabled="page === 1"
      >
        First
      </PaginationItem>
      <PaginationItem
        @click="updatePage(page - 1)"
        :disabled="page === 1"
      >
        Left
      </PaginationItem>
      <PaginationItem
        v-for="(pageValue, i) in paginatedPages"
        :key="i"
        :active="pageValue === page"
        @click="updatePage(pageValue)"
      >
        {{ pageValue }}
      </PaginationItem>
      <PaginationItem
        @click="updatePage(page + 1)"
        :disabled="page === limit"
      >
        Right
      </PaginationItem>
      <PaginationItem
        @click="updatePage(limit)"
        :disabled="page === limit"
      >
        Last
      </PaginationItem>
    </ul>
  </div>
</template>

<script>
import PaginationItem from "@/components/Pagination/PaginationItem";

export default {
  name: "Pagination",
  components: {PaginationItem},
  props: {
    limit: {
      type: Number,
      required: true
    },
    link: {
      type: String,
      default: ''
    }
  },
  emits: ['click'],
  data() {
    return {
      page: 1,
      size: 5
    }
  },
  computed: {
    paginatedPages() {
      let pages = [this.page];

      let is_left_position = true;
      let index = 1;

      while (pages.length < this.size) {
        const currentDiff = Math.ceil(index / 2);

        if (is_left_position) {
          const currentPage = this.page - currentDiff;

          if (currentPage > 0) pages.unshift(currentPage);
        } else {
          const currentPage = this.page + currentDiff;

          if (currentPage <= this.limit) pages.push(currentPage);
        }

        index++;
        is_left_position = !is_left_position;
      }

      return pages;
    }
  },
  methods: {
    updatePage(num) {
      this.page = num;

      let newRoute = null;

      if (this.$route.query.page) {
        newRoute = this.$route.fullPath.replace(/([\?\&]page=)[^\&]*/, '$1' + num);
      } else {
        newRoute = this.$route.fullPath + ['?', '&'][Object.keys(this.$route.query).length] + 'page=' + num;
      }

      this.$router.push(newRoute);
    },
    setCurrentPageByURL() {
      if (this.$route.query.page) {
        const page = Number(this.$route.query.page);
        const validated_page = Math.min(Math.max(page, 1), this.limit);

        this.updatePage(validated_page);
      }
    }
  },
  created() {
    this.setCurrentPageByURL();
  }
}
</script>
