<template>
  <main>
    <Content />
    <Popular />
    <Trailers />
    <Trends />
  </main>
</template>

<script>
import Content from "./headerContent.vue";
import Popular from "./Popular.vue";
import Trends from "./Trends.vue";
import Trailers from "./Trailers.vue";

export default {
  name: "Main",
  components: {
    Content,
    Popular,
    Trends,
    Trailers,
  },
};
</script>

<style>
.list-enter-active,
.list-leave-active {
  transition: all 0.2s ease-in-out;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
}

.imgs-enter-active,
.imgs-leave-active {
  transition: all 0.4s ease;
}
.imgs-enter-from,
.imgs-leave-to {
  opacity: 0;
  transform: translateY(-50px);
}

.popular {
  margin-top: 100px;
  margin-bottom: 20px;
}

.popular__content {
  display: flex;
  align-items: center;
}

.popular__content-title {
  font-size: 1.5em;
  margin: 0 0 4px 0;
  font-weight: 600;
}
.popular__content-category {
  display: flex;
  margin-left: 20px;
  border: 1px solid rgba(3, 37, 65);
  border-radius: 30px;
}
.popular__content-choose {
  margin-left: 10px;
  margin-right: 10px;
  transition: all 0.5s ease-in;
}

.popular__content-text {
  z-index: 99999;
  cursor: pointer;
}

.anchor {
  position: relative;
  top: 0;
  left: 0;
  z-index: 1;
  background: rgba(3, 37, 65);
  border-radius: 10px;
  color: white !important;
}

.films__content {
  display: flex;
  overflow-y: hidden;
}

.films__content-item,
.trends__content-item {
  cursor: pointer;
}
.films__content-img {
  width: 150px;
  min-width: 150px;
  border-radius: 8px;
  margin-top: 15px;
  z-index: 99999;
}

.films__content-blocks {
  display: flex;
  margin-bottom: 30px;
}

.films__content-blocks:not(:first-of-type) {
  margin-left: 20px;
}
.films__content-title {
  margin-top: 20px;
  font-weight: 700;
  color: black;
  font-size: 14px;
}
.films__content-date {
  font-size: 1em;
  margin: 0;
  padding: 0;
  color: rgba(0, 0, 0, 0.6);
  margin-top: 10px;
}

.trends {
  margin-top: 60px;
  position: relative;
}

.trends__block::before {
  content: "";
  width: 62%;
  height: 60%;
  position: absolute;
  background-image: url(https://www.themoviedb.org/assets/2/v4/misc/trending-bg-39afc2a5f77e31d469b25c187814c0a2efef225494c038098d62317d923f8415.svg);
  z-index: -5;
  bottom: 10px;
  left: 19%;
}

.trends__content-blocks {
  display: flex;
  overflow-y: hidden;
}

.trends__block {
  margin-top: 20px;
}

.isActive {
  position: relative;
  top: 0;
  left: 0;
  z-index: 1;
  background: rgba(3, 37, 65);
  border-radius: 10px;
  color: white !important;
}

.trends__content-choose {
  margin-right: 10px;
  transition: all 0.5s ease-in;
  padding-left: 10px;
  padding-right: 10px;
}

.trends__content-choose:first-of-type {
  margin-right: 0;
}
</style>
