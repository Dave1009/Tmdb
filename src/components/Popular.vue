<template>
  <section class="popular">
    <div class="container">
      <div class="popular__content">
        <h2 class="popular__content-title">What's popular</h2>
        <div class="popular__content-category">
          <div
            class="popular__content-text"
            @click="addFirst"
            :class="{ anchor: visible }"
          >
            <p class="popular__content-choose">On TV</p>
          </div>
          <div
            class="popular__content-text"
            @click="addSecond"
            :class="{ anchor: notVisible }"
          >
            <p class="popular__content-choose">In Theaters</p>
          </div>
        </div>
      </div>
      <div class="films">
        <div class="films__content">
          <transition-group name="list" tag="div" class="films__content-blocks">
            <div
              class="films__content-blocks"
              v-for="(item, index) in arr"
              :key="index"
              v-show="visible"
            >
              <div class="films__content-item">
                <router-link
                  :to="{ name: 'filmsCart', params: { id: item.id } }"
                >
                  <img
                    class="films__content-img"
                    :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                    alt=""
                  />
                </router-link>
                <h2 class="films__content-title" style="text-align: center">
                  {{ item.original_title }} <br />
                  <span> {{ item.release_date }} </span>
                </h2>
              </div>
            </div>
            <div
              class="films__content-blocks"
              v-for="(item, index) in movieArr"
              :key="index"
              v-show="notVisible"
            >
              <router-link :to="{ name: 'filmsCart', params: { id: item.id } }">
                <div class="films__content-item">
                  <img
                    class="films__content-img"
                    :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                    alt="films"
                  />
                  <h2 class="films__content-title">
                    {{ item.original_title }}
                  </h2>
                  <p class="films__content-date">
                    {{ item.release_date }}
                  </p>
                </div>
              </router-link>
            </div>
          </transition-group>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      name: "Popular",
      arr: [],
      movieArr: [],
      visible: true,
      notVisible: false,
    };
  },
  methods: {
    addFirst() {
      this.notVisible = false;
      this.visible = true;
    },
    addSecond() {
      this.visible = false;
      this.notVisible = true;
    },
    fetchPost() {
      fetch(
        `https://api.themoviedb.org/3/movie/popular?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US&page=1`
      )
        .then((response) => response.json())
        .then((data) => {
          this.arr = data["results"];
          console.log(this.arr);
        });
    },
    fetchPostMovies() {
      fetch(
        ` https://api.themoviedb.org/3/movie/now_playing?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US&page=1`
      )
        .then((response) => response.json())
        .then((data) => {
          this.movieArr = data["results"];
        });
    },
  },
  mounted() {
    this.fetchPost();
    this.fetchPostMovies();
  },
};
</script>
