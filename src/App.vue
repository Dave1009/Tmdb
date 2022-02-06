<template>
  <link
    rel="stylesheet"
    href="https://pro.fontawesome.com/releases/v5.10.0/css/all.css"
    integrity="sha384-AYmEC3Yw5cVb3ZcuHtOA93w35dYTsvhLPVnYs9eStHfGJvOvKxVfELGroGkvsg+p"
    crossorigin="anonymous"
  />
  <Header />
  <router-view />
  <Footer />
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
  text-decoration: none;
  list-style: none;
  font-family: "Roboto";
}
.container {
  margin: 0 auto;
  padding: 0 15px;
  max-width: 1140px;
}

.container-fluid {
  margin: 0 auto;
  padding: 0 15px;
  max-width: 1440px;
}

@font-face {
  font-family: "Roboto";
  src: local(Roboto), url(assets/fonts/Roboto-Regular.ttf) format("truetype");
}
@font-face {
  font-family: "Mono";
  src: local(Roboto), url(assets/fonts/SpaceMono-Bold.ttf) format("truetype");
}

::-webkit-scrollbar-thumb {
  border-radius: 10px; /*Закругление ползунка*/
  background-color: #ccc; /*Цвет ползунка*/
  padding-left: 10px;
}
::-webkit-scrollbar {
  width: 6px; /*Толщина скролла*/
  height: 10px;
}
</style>
