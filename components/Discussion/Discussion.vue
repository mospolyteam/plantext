<template>
  <NuxtLink :to="link" class="discussion">
    <h3 class="discussion__title">{{ discussion.title }}</h3>
    <p class="discussion__link">
      Поучаствовать
      <Icon name="arrow" width="16" height="16">
        <IconArrow/>
      </Icon>
    </p>
  </NuxtLink>
</template>

<script>
import Icon from "@/components/Icon/Icon";
import IconArrow from "@/components/Icon/IconArrow";

export default {
  name: "Discussion",
  components: {IconArrow, Icon},
  props: {
    discussion: {
      id: Number,
      title: String
    }
  },
  computed: {
    link() {
      return '/discussion/' + this.discussion.id
    }
  }
}
</script>

<style>
  .discussion {
    height: 260px;
    padding: 30px 20px 25px;
    background-color: #C08B74;
    display: flex;
    transition-property: background-color, color;
    transition-duration: .5s, .5s;
    transition-timing-function: ease, ease;
  }

  .discussion:hover {
    background-color: #A569BF;
    color: #fff;
  }

  .discussion__title {
    max-width: 70%;
  }

  .discussion__link {
    margin-top: auto;
    margin-left: auto;
    display: flex;
    align-items: center;
    gap: 5px;
  }
</style>
