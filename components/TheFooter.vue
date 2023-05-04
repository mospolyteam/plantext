<template>
  <footer class="footer">
    <div class="container">
      <div class="row">
        <hr/>
        <div class="footer__content">
          <Navigation column :items="menu.first" class="footer__navigation"/>
          <Navigation column :items="menu.second" class="footer__navigation"/>
          <FooterSocials />
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import Navigation from "~/components/Navigation/Navigation.vue";
import FooterSocials from "~/components/Footer/FooterSocials.vue";

export default {
  name: "TheFooter",
  components: {FooterSocials, Navigation},
  props: {},
  data() {
    return {
      menu: {
        first: [
          {
            text: 'Книги',
            link: '/book'
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
            text: 'Правила сообщества',
            link: '/rules'
          }
        ],
        second: [
          {
            text: 'Станьте нашим писателем',
            link: '/apply'
          },
          {
            text: 'О форуме',
            link: '/about'
          },
          {
            text: 'Контакты',
            link: '/contacts'
          }
        ]
      }
    }
  },
  computed: {},
  methods: {},
  created() {
  },
  mounted() {
  }
}
</script>
<style>
.footer {
  height: 450px;
  background-image: url('@/assets/images/footer.png');
  background-repeat: no-repeat;
  background-position: right;
}

.footer__content {
  display: flex;
  gap: 100px;
  padding-top: 50px;
}

.footer__navigation {
  max-width: 140px;
}
</style>
