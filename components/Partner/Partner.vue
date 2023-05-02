<template>
  <NuxtLink :to="partner.link" class="partner">
    <img :src="partner.image" :alt="partner.alt" class="partner__image">
  </NuxtLink>
</template>

<script>
export default {
    name: "Partner",
    props: {
      partner: {
        id: Number,
        link: String,
        image: String,
        alt: String
      }
    }
}
</script>

<style>
  .partner {
    display: block;
  }

  .partner__image {
    width: 100%;
  }
</style>
