<template>
  <main>
    <section class="preview">
      <div class="container">
        <div class="preview__head">
          <ul class="preview__head-list">
            <li class="preview__head-link">
              <a
                href="#!"
                class="preview__head-link"
                :class="{ active: firstLink }"
                @click="addFirstStyle"
                style="color: black"
                >Обзор <span><i class="fas fa-caret-down"></i></span
              ></a>
            </li>
            <li class="preview__head-link">
              <a
                href="#!"
                class="preview__head-link"
                @click="addSecondStyle"
                :class="{ active: secondLink }"
                style="color: black"
                >Медиа <span><i class="fas fa-caret-down"></i></span
              ></a>
            </li>
            <li class="preview__head-link">
              <a
                href="#!"
                class="preview__head-link"
                @click="addThirdStyle"
                :class="{ active: thirdLink }"
                style="color: black"
                >Фандом <span><i class="fas fa-caret-down"></i></span
              ></a>
            </li>
            <li class="preview__head-link">
              <a
                href="#!"
                class="preview__head-link"
                @click="addFourStyle"
                :class="{ active: fourLink }"
                style="color: black"
                >Поделиться <span><i class="fas fa-caret-down"></i></span
              ></a>
            </li>
          </ul>
        </div>
      </div>
      <div class="preview__content" style="position: relative">
        <img
          style="
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 0;
            object-fit: cover;
            z-index: -33;
          "
          :src="`https://www.themoviedb.org/t/p/w1920_and_h800_multi_faces/${arr.backdrop_path}`"
          alt=""
        />
        <div class="container">
          <div class="preview__content-total">
            <div class="preview__content-block">
              <div class="preview__content-items">
                <img
                  class="preview__content-img"
                  :src="`https://www.themoviedb.org/t/p/w300_and_h450_bestv2/${arr.poster_path}`"
                  alt=""
                />
                <div class="preview__content-now">
                  <img
                    src="https://www.themoviedb.org/t/p/original/As8vTHasikgyhZPkSOI9QzAst4L.jpg"
                    alt=""
                    style="width: 36px; height: 36px"
                  />
                  <div class="preview__content-img-text">
                    <h4>Now Streaming</h4>
                    <p>Watch now</p>
                  </div>
                </div>
              </div>
            </div>
            <div class="preview__content-block">
              <h1 class="preview__content-title">
                {{ arr.original_title }}
              </h1>
              <div class="preview__content-desk">
                <span class="preview__content-desk-age">{{
                  arr.release_date
                }}</span>
                <span
                  style="font-size: 14px"
                  v-for="(item, index) in country"
                  :key="index"
                  >({{ item.iso_3166_1 }})</span
                >
                <p
                  class="preview__content-description"
                  v-for="(item, index) in genres"
                  :key="index"
                >
                  {{ item.name }} |
                </p>
                <span> <i class="fas fa-circle"></i></span>
                <span>1h</span>
              </div>

              <ul class="preview__content-list">
                <li class="preview__content-link">
                  <h2>
                    User Score
                    <span>{{ arr.vote_average }}</span>
                  </h2>
                </li>
                <li class="preview__content-link">
                  <a href="#!"
                    ><img
                      src="https://www.themoviedb.org/assets/2/v4/glyphicons/basic/glyphicons-basic-159-thumbnails-list-white-c260ea972eebf812289fd3c41d0d2c1dff33ecbcd62be13fba8eeaf9de173789.svg"
                      alt=""
                    />
                  </a>
                </li>
                <li class="preview__content-link">
                  <a href="#!">
                    <img
                      src="https://www.themoviedb.org/assets/2/v4/glyphicons/basic/glyphicons-basic-13-heart-white-28d2cc2d6418c5047efcfd2438bfc5d109192671263c270993c05f130cc4584e.svg"
                      alt=""
                  /></a>
                </li>
                <li class="preview__content-link">
                  <a href="#!">
                    <img
                      src="https://www.themoviedb.org/assets/2/v4/glyphicons/basic/glyphicons-basic-73-bookmark-white-432e98d550b7e4c80b06272c49475b0db85a60f6fae450420713004b3c9d3ffd.svg"
                      alt=""
                  /></a>
                </li>
                <li class="preview__content-link">
                  <a href="#!">
                    <img
                      src="https://www.themoviedb.org/assets/2/v4/glyphicons/basic/glyphicons-basic-49-star-white-5c85220678b312aea9599d5f12ad858a9e7df226de51ef8b6b699023ffeda5fa.svg"
                      alt=""
                  /></a>
                </li>
                <li>
                  <i class="fas fa-play"><span>Воспроизвести трейлер</span></i>
                </li>
              </ul>
              <h3 class="preview__content-view">{{ arr.tagline }}</h3>
              <h2 class="preview__content-text-title">Overview</h2>
              <p class="preview__content-text">
                {{ arr.overview }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: "filmsCart",
  props: ["id"],
  data() {
    return {
      arr: [],
      genres: [],
      creators: [],
      country: [],
      firstLink: true,
      secondLink: false,
      thirdLink: false,
      fourLink: false,
    };
  },
  created() {
    this.fetchPost(this.id);
  },
  watch: {
    movieId() {
      this.fetchPost(this.id);
    },
  },
  methods: {
    fetchPost(id) {
      fetch(
        `https://api.themoviedb.org/3/movie/${id}?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US`
      )
        .then((response) => response.json())
        .then((data) => {
          this.arr = data;
          this.genres = data.genres;
          this.creators = data.name;
          this.country = data.production_countries;
          console.log(this.arr);
        });
    },
    addFirstStyle() {
      (this.firstLink = true),
        (this.secondLink = false),
        (this.thirdLink = false),
        (this.fourLink = false);
    },
    addSecondStyle() {
      (this.firstLink = false),
        (this.secondLink = true),
        (this.thirdLink = false),
        (this.fourLink = false);
    },
    addThirdStyle() {
      (this.firstLink = false),
        (this.secondLink = false),
        (this.thirdLink = true),
        (this.fourLink = false);
    },
    addFourStyle() {
      (this.firstLink = false),
        (this.secondLink = false),
        (this.thirdLink = false),
        (this.fourLink = true);
    },
  },
  mounted() {
    console.log(this.genres);
  },
};
</script>

<style>
.preview__content {
  padding-bottom: 40px;
  padding-top: 40px;
  background: rgba(61, 59, 59, 0.829);
}
.preview__content-block {
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.preview__content-block:last-of-type {
  margin-left: 40px;
}
.preview__content-total {
  display: flex;
  align-items: center;
}
.preview__head {
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.preview__head-list {
  display: flex;
}
.preview__head-link {
  margin-left: 25px;
  padding-left: 5px;
}
.preview__head-link span {
  margin-left: 3px;
}
.preview__head-link:first-of-type {
  margin-left: 0;
}
.preview__head-link .active {
  border-bottom: 4px solid rgb(1, 180, 228);
  padding-bottom: 11px;
}

.preview__content-img {
  min-width: 300px;
  width: 300px;
  height: 450px;
}
.preview__content-now {
  display: flex;
  justify-content: center;
  background: rgb(3, 37, 65);
  padding: 10px 12px;
  color: white;
  margin-top: -5px;
  border-bottom-right-radius: 8px;
  border-bottom-left-radius: 8px;
}
.preview__content-img-text {
  margin-left: 15px;
}
.preview__content-img-text h3 {
  opacity: 0.6;
}
.preview__content-img-text p {
  font-weight: 600;
}
.preview__content-title {
  font-size: 2.2rem;
  font-weight: 700;
}
.preview__content-desk {
  margin-top: 5px;
  margin-bottom: 15px;
  display: flex;
  align-items: center;
}
.preview__content-desk-age {
  border: 1px solid rgba(255, 255, 255, 0.6);
  color: rgba(255, 255, 255, 0.6);
  padding: 3px;
  font-size: 12px;
  margin-right: 8px;
}
.preview__content-description {
  margin-left: 15px;
}
.preview__content-desk i {
  font-size: 4px;
  padding: 5px 5px 10px 5px;
}
.preview__content-list {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
}
.preview__content-link h2 {
  margin-right: 7px;
}
.preview__content-list li img {
  width: 1em;
  height: 1em;
  background: rgb(3, 37, 65);
  padding: 15px;
  border-radius: 50%;
  margin-right: 14px;
}
.preview__content-list li span {
  margin-left: 8px;
}
.preview__content-view {
  font-size: 1.1em;
  font-weight: 400;
  font-style: italic;
  opacity: 0.7;
  margin-top: 24px;
  margin-bottom: 15px;
}
.preview__content-text-title {
  font-size: 1.3em;
  margin-bottom: 14px;
}
.preview__content-text {
  font-size: 1em;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
.preview__content-creators {
  display: flex;
  margin-top: 25px;
}
.preview__content-name {
  font-size: 1em;
  opacity: 0.9;
}
.preview__content-names {
  margin-left: 25px;
}
.preview__content-creator {
  font-size: 14px;
  opacity: 0.8;
}
</style>
