<template>
  <div>
    <TheHeader/>
    <Nuxt/>
    <TheFooter/>
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader";
import TheFooter from "@/components/TheFooter";

export default {
  components: {TheFooter, TheHeader}
}
</script>
