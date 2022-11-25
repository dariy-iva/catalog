<template>
  <section class="clothes">
    <div
      class="clothes__image"
      :style="`background-image: url('${photoList[0] || '#'}')`"
    />

    <ul class="clothes__list">
      <li
        v-for="(photo, index) in photoList.slice(1, 5)"
        :key="photo"
        :style="`background-image: url('${photo || '#'}')`"
        class="clothes__image"
      >
        <div
          v-if="index === 2"
          class="clothes__overlay"
        >
          <button
            type="button"
            title="копировать"
            class="clothes__copy"
            aria-label="скопировать"
          />

          <div class="clothes__info">
            <nuxt-link
              to="/"
              no-prefetch
              title="Узнай, что на мне"
              class="clothes__basket"/>
            <span class="clothes__description clothes__text">
              Узнай, что на мне
            </span>
          </div>

          <span class="clothes__likes clothes__text">200</span>
        </div>
      </li>
    </ul>

  </section>
</template>

<script>
export default {
  name: "ClothesLooks",

  data() {
    return {
      photoList: [
        '/images/products/looks/look_1.webp',
        '/images/products/looks/look_2.webp',
        '/images/products/looks/look_3.webp',
        '/images/products/looks/look_4.webp',
        '/images/products/looks/look_5.webp',
      ]
    }
  },
}
</script>

<style scoped>
.clothes {
  display: grid;
  grid-template-columns: repeat(2, 49.4%);
  justify-content: space-between;
}

.clothes__image {
  aspect-ratio: 10 / 10.03;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  transition: filter .3s;
  cursor: pointer;
}

.clothes__image:hover {
  filter: drop-shadow(10px 10px 10px var(--dark-gray-color))
}

.clothes__list {
  padding: 0;
  margin: 0;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 16px;
  list-style-type: none;
}

.clothes__overlay {
  position: relative;
  width: 100%;
  height: 100%;
}

.clothes__overlay::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: block;
  background-color: var(--brand-black-color);
  opacity: .7;
}

.clothes__copy {
  position: absolute;
  top: 12px;
  right: 12px;
  z-index: 1;
  width: 24px;
  height: 24px;
  mask-size: 16px;
  -webkit-mask-size: 16px;
  mask-position: center;
  -webkit-mask-position: center;
  mask-repeat: no-repeat;
  -webkit-mask-repeat: no-repeat;
  mask-image: url("static/images/icons/copy.svg");
  -webkit-mask-image: url("static/images/icons/copy.svg");
  background-color: var(--white-color);
  cursor: pointer;
  border: none;
  outline: none;
  transition: background-color .3s;
}

.clothes__copy:hover {
  background-color: var(--yellow-color);
}

.clothes__info {
  position: absolute;
  top: 42.99%;
  left: 0;
  right: 0;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.clothes__basket {
  display: block;
  width: 48px;
  height: 48px;
  cursor: pointer;
  mask-size: 34px;
  -webkit-mask-size: 34px;
  mask-position: center;
  -webkit-mask-position: center;
  mask-repeat: no-repeat;
  -webkit-mask-repeat: no-repeat;
  mask-image: url("static/images/icons/basket.svg");
  -webkit-mask-image: url("static/images/icons/basket.svg");
  background-color: var(--white-color);
  transition: background-color .3s;
}

.clothes__basket:hover {
  background-color: var(--yellow-color);
}

.clothes__text {
  font-weight: 400;
  font-size: 14px;
  line-height: 1.43;
  letter-spacing: 0.04em;
  color: var(--white-color);
}

.clothes__likes {
  position: absolute;
  left: 0;
  right: 0;
  justify-content: center;
  bottom: 20px;
  z-index: 1;
  display: flex;
  align-items: center;
}

.clothes__likes::before {
  content: "";
  display: block;
  width: 16px;
  height: 16px;
  mask-size: cover;
  -webkit-mask-size: cover;
  mask-position: center;
  -webkit-mask-position: center;
  mask-repeat: no-repeat;
  -webkit-mask-repeat: no-repeat;
  mask-image: url("static/images/icons/like.svg");
  -webkit-mask-image: url("static/images/icons/like.svg");
  background-color: var(--white-color);
  margin-right: 2px;
}

@media (max-width: 1023px) {
  .clothes__description {
    display: none;
  }

  .clothes__likes {
    bottom: 5px;
  }
}

@media (max-width: 767px) {
  .clothes {
    grid-template-columns: 1fr;
  }

  .clothes__overlay {
    display: none;
  }
}

</style>
