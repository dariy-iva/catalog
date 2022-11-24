<template>
  <div class="page">
    <Nuxt/>
  </div>
</template>

<script>
export default {
  name: "default",

  head() {
    return {
      bodyAttrs: {
        class: 'body'
      }
    }
  },
}
</script>

<style>
@import "static/fonts/open_sans/OpenSans.css";

.body {
  margin: 0 auto;
  font-family: 'Open Sans', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.page {
  position: relative;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  --black-color: #000;
  --white-color: #fff;
  --brand-black-color: #333;
  --light-gray-color: #C4C4C4;
  --gray-color: #F2F2F2;
  --dark-gray-color: #828282;
  background-color: var(--white-color);
}

</style>
