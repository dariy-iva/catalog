<template>
  <footer class="footer">
    <div class="footer__container wrapper">
      <div
        v-for="list in linkLists"
        :key="list.title"
        class="footer__column"
      >
        <h3 class="footer__title">
          {{ list.title }}
        </h3>

        <ul class="footer__nav-links">
          <li
            v-for="link in list.links"
            :key="link.label">
            <nuxt-link
              exact
              :to="link.link"
              class="footer__nav-link footer__text link-hover">
              {{ link.label }}
            </nuxt-link>
          </li>
        </ul>
      </div>

      <div class="footer__subscription">
        <h3 class="footer__title footer__title_form">Узнайте первыми о новинках и акциях</h3>

        <SubscriptionForm/>
      </div>
    </div>

  </footer>

</template>

<script>
import {navigationLinks} from "assets/constants/navigationLinks";
import SubscriptionForm from "~/components/SubscriptionForm";

export default {
  name: "Footer",

  components: {
    SubscriptionForm
  },

  computed: {
    linkLists() {
      return [
        {title: 'покупателям', links: navigationLinks.products},
        {title: 'о нас', links: navigationLinks.about},
      ];
    },
  },
}
</script>

<style scoped>
.footer {
  padding: 130px 0 70px;
}

.footer__container {
  display: grid;
  justify-content: center;
  grid-template-columns: 24.1% 24.1% 32.5%;
  column-gap: 16px;
}

.footer__title {
  margin: 0;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.5;
  letter-spacing: .04em;
  text-transform: uppercase;
  color: var(--brand-black-color);
}

.footer__title_form {
  margin-bottom: 33px;
}

.footer__text {
  font-weight: 400;
  font-size: 14px;
  line-height: 1.43;
  letter-spacing: .04em;
}

.footer__nav-links {
  margin: 16px 0 0;
  padding: 0;
  list-style-type: none;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.footer__nav-link {
  text-decoration: none;
}

@media (max-width: 767px) {
  .footer {
    padding: 42px 20px 186px;
  }

  .footer__container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    grid-column-gap: 0;
  }

  .footer__column {
    width: calc(50% - 4.5px);
  }

  .footer__subscription {
    margin-top: 58px;
    width: 100%;
  }

  .footer__title_form {
    margin-bottom: 17px;
  }
}

</style>
