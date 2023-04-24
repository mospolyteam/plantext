<template>
  <div class="pagination">
    <ul class="pagination__list">
      <PaginationItem
        @click="updatePage(1)"
        :disabled="page === 1"
      >
        <svg width="20" height="15" viewBox="0 0 20 15" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M4.93665 7.49972L9.51135 11.8596L7.22481 14.041L0.363564 7.49972L7.22481 0.958432L9.51135 3.13989L4.93665 7.49972Z"
                fill="currentColor"/>
          <path d="M14.93665 7.49972L19.51135 11.8596L17.22481 14.041L10.363564 7.49972L17.22481 0.958432L19.51135 3.13989L14.93665 7.49972Z"
                fill="currentColor"/>
        </svg>
      </PaginationItem>
      <PaginationItem
        @click="updatePage(page - 1)"
        :disabled="page === 1"
      >
        <svg width="10" height="15" viewBox="0 0 10 15" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M4.93665 7.49972L9.51135 11.8596L7.22481 14.041L0.363564 7.49972L7.22481 0.958432L9.51135 3.13989L4.93665 7.49972Z"
                fill="currentColor"/>
        </svg>
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
        <svg width="10" height="15" viewBox="0 0 10 15" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M5.05589 7.50028L0.524902 3.14044L2.78959 0.958984L9.58527 7.50028L2.78959 14.0416L0.524902 11.8601L5.05589 7.50028Z"
                fill="currentColor"/>
        </svg>
      </PaginationItem>
      <PaginationItem
        @click="updatePage(limit)"
        :disabled="page === limit"
      >
        <svg width="20" height="15" viewBox="0 0 20 15" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M5.05589 7.50028L0.524902 3.14044L2.78959 0.958984L9.58527 7.50028L2.78959 14.0416L0.524902 11.8601L5.05589 7.50028Z"
                fill="currentColor"/>
          <path d="M15.05589 7.50028L10.524902 3.14044L12.78959 0.958984L19.58527 7.50028L12.78959 14.0416L10.524902 11.8601L15.05589 7.50028Z"
                fill="currentColor"/>
        </svg>
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

<style>
  ul {
    list-style: none;
  }

  button {
    border: none;
    background: none;
  }

  .pagination__list {
    display: flex;
  }


</style>
