<template>
  <ul class="footer__contacts">
    <li>
      <a class="footer__contact" href="tel:+78005553535">
        <IconTel/>
        <span>+7 (800) 555-35-35</span>
      </a>
    </li>
    <li>
      <a class="footer__contact" href="mailto:mospolyteam@gmail.com">
        <IconMail/>
        <span>mospolyteam@gmail.com</span>
      </a>
    </li>
    <li>
      <ul class="footer__socials">
        <li class="footer__social">
          <a href="#">
            <IconTelegram/>
          </a>
        </li>
        <li class="footer__social">
          <a href="#">
            <IconFacebook/>
          </a>
        </li>
        <li class="footer__social">
          <a href="#">
            <IconWhatsapp/>
          </a>
        </li>
      </ul>
    </li>
  </ul>
</template>

<script>
import IconTel from "~/components/Icon/IconTel.vue";
import IconMail from "~/components/Icon/IconMail.vue";
import IconTelegram from "~/components/Icon/IconTelegram.vue";
import IconFacebook from "~/components/Icon/IconFacebook.vue";
import IconWhatsapp from "~/components/Icon/IconWhatsapp.vue";

export default {
  name: "FooterSocials",
  components: {IconWhatsapp, IconFacebook, IconTelegram, IconMail, IconTel},
  props: {},
  data() {
    return {}
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
.footer__contacts {
  display: flex;
  flex-direction: column;
  gap: 30px;
  margin-left: auto;
  margin-right: 400px;
}

.footer__contact {
  display: flex;
  align-items: center;
  gap: 20px;
}

.footer__socials {
  display: flex;
  align-items: center;
  gap: 40px;
}
</style>
