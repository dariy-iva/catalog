<template>
  <div class="page">
    <Header/>

    <main class="content">
      <Nuxt/>
    </main>

    <Footer/>
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
  --yellow-color: #ffa200;
  --red-color: #ff0000;
  background-color: var(--white-color);
}

.content {
  padding-top: calc(26px + 40px);
  flex-grow: 1;
}

.wrapper {
  margin: 0 auto;
  max-width: 1390px;
}

.link-hover {
  transition: color .3s;
}

a.link-hover:hover {
  color: var(--yellow-color);
}

@media (max-width: 1440px) {
  .wrapper {
    margin: 0 25px;
  }
}

@media (max-width: 767px) {
  .content {
    padding-top: 68px;
  }

  .wrapper {
    margin: 0;
  }
}

</style>
