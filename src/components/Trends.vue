<template>
  <section class="trends">
    <div class="container">
      <div class="popular__content">
        <h2 class="popular__content-title">In Trends</h2>
        <div class="popular__content-category">
          <div class="popular__content-text">
            <p
              class="trends__content-choose"
              @click="addActive"
              :class="{ isActive: active }"
            >
              Today
            </p>
          </div>
          <div class="popular__content-text">
            <p
              class="trends__content-choose"
              :class="{ isActive: notActive }"
              @click="addNotActive"
            >
              On this week
            </p>
          </div>
        </div>
      </div>
      <div class="trends__block">
        <div class="trends__content">
          <transition-group
            name="list"
            tag="div"
            class="trends__content-blocks"
          >
            <div
              class="films__content-blocks"
              v-for="(item, index) in trends"
              :key="index"
              v-show="active"
            >
              <router-link :to="{ name: 'filmsCart', params: { id: item.id } }">
                <div class="films__ content-item">
                  <img
                    class="films__content-img"
                    :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                    alt=""
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
            <div
              class="films__content-blocks"
              v-for="(item, index) in trendsWeek"
              :key="index"
              v-show="notActive"
            >
              <router-link :to="{ name: 'filmsCart', params: { id: item.id } }">
                <div class="films__content-item">
                  <img
                    class="films__content-img"
                    :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                    alt=""
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
      name: "Trends",
      trends: [],
      trendsWeek: [],
      active: true,
      notActive: false,
    };
  },
  methods: {
    addActive() {
      this.active = true;
      this.notActive = false;
    },
    addNotActive() {
      this.notActive = true;
      this.active = false;
    },
    fetchPostTrends() {
      fetch(
        `https://api.themoviedb.org/3/movie/upcoming?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US&page=1`
      )
        .then((response) => response.json())
        .then((data) => {
          this.trends = data["results"];
        });
    },
    fetchPostTrendsWeek() {
      fetch(
        `https://api.themoviedb.org/3/movie/upcoming?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US&page=2`
      )
        .then((response) => response.json())
        .then((data) => {
          this.trendsWeek = data["results"];
        });
    },
  },
  mounted() {
    this.fetchPostTrends();
    this.fetchPostTrendsWeek();
  },
};
</script>
