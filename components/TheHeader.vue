<template>
  <header class="header">
    <div class="container">
      <div class="row">
        <div class="header__top">
          <form action="#" class="header__form">
            <FormField>
              <FormLabel name="search"/>
              <FormInput v-model="searchValue" name="search"/>
            </FormField>
          </form>
          <TheLogo class="header__logo"/>
          <ul class="header__functions">
            <li class="header__function">
              <button class="header__button">
                <IconNotification/>
              </button>
            </li>
            <li class="header__function">
              <button class="header__button">
                <IconHeart/>
              </button>
            </li>
            <li class="header__function">
              <button class="header__button">
                <IconProfile/>
              </button>
            </li>
          </ul>
        </div>
        <nav class="header__nav nav">
          <Navigation class="nav__menu" :items="menu"/>
        </nav>
      </div>
    </div>
  </header>
</template>

<script>
import FormField from "~/components/Form/FormField.vue";
import FormLabel from "~/components/Form/FormLabel.vue";
import TheLogo from "~/components/TheLogo.vue";
import Navigation from "~/components/Navigation/Navigation.vue";
import FormInput from "~/components/Form/FormInput.vue";
import IconNotification from "~/components/Icon/IconNotification.vue";
import IconHeart from "~/components/Icon/IconHeart.vue";
import IconProfile from "~/components/Icon/IconProfile.vue";

export default {
  name: "TheHeader",
  components: {IconProfile, IconHeart, IconNotification, FormInput, Navigation, TheLogo, FormLabel, FormField},
  data() {
    return {
      searchValue: '',
      menu: [
        {
          text: 'Главная',
          link: '/'
        },
        {
          text: 'Книги',
          link: '/books'
        },
        {
          text: 'Статьи',
          link: '/articles'
        },
        {
          text: 'Обсуждения',
          link: '/discussions'
        },
        {
          text: 'Подборки',
          link: '/'
        },
        {
          text: 'Цитаты',
          link: '/'
        }
      ]
    }
  }
}
</script>
<style>
.header {
  margin-bottom: 15px;
}

.header__top {
  height: 100px;
  margin-bottom: 20px;
  border-bottom: 1px solid #1B1917;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
}

.header__logo {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}

.nav {
  display: flex;
  justify-content: center;
}

.header__functions {
  display: flex;
  align-items: center;
  gap: 50px;
}

.header__function {
  height: min-content;
}
</style>
