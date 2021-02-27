<template>
  <Header />
  <Introduction />
  <Shorten />
  <Statistics />
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import Introduction from "./components/Introduction.vue";
import Shorten from "./components/Shorten.vue";
import Statistics from "./components/Statistics.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Introduction,
    Shorten,
    Statistics,
    Footer,
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@500;700&display=swap");
@import "./components/utility/utility";

#app {
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $neutral-2;
  min-height: inherit;

  display: flex;
  flex-direction: column;
  min-width: 375px;
}
</style>
