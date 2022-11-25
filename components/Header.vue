<template>
  <header class="header">
    <div class="header__container wrapper">
      <nuxt-link
        exact
        to="/"
        class="header__logo link-hover">
        logo
      </nuxt-link>

      <nav class="header__navigation">
        <ul class="header__nav-links">
          <li
            v-for="item in links"
            :key="item.name">
            <nuxt-link
              exact
              :to="item.link"
              no-prefetch
              :class="`header__nav-link header__nav-link_to_${item.name}`"/>
          </li>
        </ul>

        <button
          type="button"
          class="header__menu-button"
          aria-label="открыть меню"
        />
      </nav>
    </div>
  </header>
</template>

<script>
import {navigationLinks} from "assets/constants/navigationLinks";

export default {
  name: "Header",

  computed: {
    links() {
      return navigationLinks.user;
    }
  }
}
</script>

<style scoped>
.header {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, .1);
}

.header__container {
  padding: 8px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header__logo {
  font-weight: 700;
  font-size: 22px;
  line-height: .73;
  letter-spacing: .04em;
  text-transform: uppercase;
  text-decoration: none;
}

.header__navigation {
  display: flex;
  gap: 28px;
}

.header__nav-links {
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
  gap: 28px;
  list-style-type: none;
}

.header__nav-link {
  width: 24px;
  height: 24px;
  display: block;
  mask-size: 16px;
  -webkit-mask-size: 16px;
  mask-position: center;
  -webkit-mask-position: center;
  mask-repeat: no-repeat;
  -webkit-mask-repeat: no-repeat;
  background-color: var(--brand-black-color);
  transition: background-color .3s;
  box-sizing: border-box;
}

.header__nav-link:hover {
  background-color: var(--yellow-color);
}

.header__nav-link_to_account {
  mask-image: url("static/images/icons/account.svg");
  -webkit-mask-image: url("static/images/icons/account.svg");
}

.header__nav-link_to_favourites {
  mask-image: url("static/images/icons/favourites.svg");
  -webkit-mask-image: url("static/images/icons/favourites.svg");
}

.header__nav-link_to_basket {
  mask-image: url("static/images/icons/basket.svg");
  -webkit-mask-image: url("static/images/icons/basket.svg");
}

.header__menu-button {
  display: none;
}

@media (max-width: 767px) {
  .header {
    box-shadow: none;
  }

  .header__container {
    padding: 18px 20px 26px;
  }

  .header__menu-button {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 24px;
    height: 24px;
    border: none;
    background: none;
    cursor: pointer;
  }

  .header__menu-button::before {
    content: "";
    display: block;
    min-width: 18px;
    height: 12px;
    border-top: 1px solid var(--brand-black-color);
    border-bottom: 1px solid var(--brand-black-color);
    box-sizing: border-box;
    transition: border .3s;
  }

  .header__menu-button:hover::before {
    border-bottom-color: var(--yellow-color);
    border-top-color: var(--yellow-color);
  }

  .header__menu-button::after {
    position: absolute;
    top: auto;
    content: "";
    display: block;
    width: 18px;
    border-top: 1px solid var(--brand-black-color);
    box-sizing: border-box;
    transition: border .3s;
  }

  .header__menu-button:hover::after {
    border-top-color: var(--yellow-color);
  }
}

</style>
