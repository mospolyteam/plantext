<template>
    <a href="#" class="article">
        <img class="article__preview" 
            :src="`${article.preview}`" 
            :alt="article.title"
        >
        <p class="article__title">{{ article.title }}</p>
    </a>
</template>

<script>
export default {
    name: "Article",
    props: {
        article: {
            preview: String,
            title: String,
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

<style>
    .article {
        display: block;
        max-width: 387px;
    }
    .article:hover {
        text-decoration: underline;
    }
    .article__title {
        font-size: 24px;
        max-width: 367px;
    }
</style>
