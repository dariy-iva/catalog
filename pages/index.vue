<template>
  <div class="products wrapper">
    <ProductCard/>

    <nuxt-link
      to="/"
      no-prefetch
      class="products__all link-hover"
    >
      Посмотреть все стили
    </nuxt-link>

    <ClothesLooks/>
  </div>
</template>

<script>
import ProductCard from "~/components/ProductCard";
import ClothesLooks from "~/components/ClothesLooks";

export default {
  name: 'IndexPage',

  components: {
    ProductCard,
     ClothesLooks
  }
}
</script>

<style scoped>
.products {
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.products__all {
  width: fit-content;
  align-self: center;
  font-weight: 400;
  font-size: 14px;
  line-height: 1.43;
  letter-spacing: 0.04em;
  text-decoration-line: underline;
  color: var(--brand-black-color);
}
</style>
