<template>
  <header class="header">
    <div class="container">
      <Row class="header__top">
        <form action="#" class="header__form col-md-3">
          <FormField>
            <FormLabel name="search" hidden/>
            <FormInput v-model="searchValue" name="search">
              <template v-slot:icon>
                <IconSearch />
              </template>
            </FormInput>
          </FormField>
        </form>
        <TheLogo class="header__logo offset-md-2 col-md-2"/>
        <ul class="header__functions offset-md-2 col-md-3">
          <HeaderFunction>
            <IconNotification/>
          </HeaderFunction>
          <HeaderFunction>
            <IconHeart/>
          </HeaderFunction>
          <HeaderFunction>
            <IconProfile/>
          </HeaderFunction>
        </ul>
      </Row>
      <hr/>
      <Row>
        <nav class="header__nav nav col-12">
          <Navigation class="nav__menu" :items="menu"/>
        </nav>
      </Row>
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
import IconSearch from "~/components/Icon/IconSearch.vue";
import Row from "~/components/Row/Row.vue";
import HeaderFunction from "~/components/Header/HeaderFunction.vue";

export default {
  name: "TheHeader",
  components: {
    HeaderFunction,
    Row, IconProfile, IconHeart, IconNotification, IconSearch, FormInput, Navigation, TheLogo, FormLabel, FormField},
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
  height: 90px;
  margin-bottom: 10px;
  align-items: center;
}

.nav {
  display: flex;
  justify-content: center;
}

.header__functions {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 50px;
}

.header__function {
  height: min-content;
}

.header__nav {
  margin-top: 25px;
}

.header__logo {
  text-align: center;
}
</style>
