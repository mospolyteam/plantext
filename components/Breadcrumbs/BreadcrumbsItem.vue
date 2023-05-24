<template>
  <NuxtLink class="breadcrumbs__item" :to="link">
    <slot/>
  </NuxtLink>
</template>

<script>
export default {
    name: "BreadcrumbsItem",
    props: {
      link: {
        type: String,
        default: ''
      }
    },
    data() {
        return {}
    },
    computed: {},
    methods: {},
    created() {},
    mounted() {}
}
</script>
