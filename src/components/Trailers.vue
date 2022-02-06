<template>
  <section class="trailers">
    <div class="container">
      <div class="trailers__content">
        <div class="trailers__content-block" style="position: relative">
          <div
            class="trailers__content-bg-img"
            v-for="(item, index) in newArr"
            :key="index"
          >
            <img
              style="
                width: 100%;
                height: 100%;
                position: absolute;
                top: 0;
                left: 0;
                opacity: 0.9;
                object-fit: cover;
                z-index: -1;
              "
              :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.backdrop_path}`"
              alt=""
            />
          </div>
          <div class="trailers__content-head">
            <h2 class="trailers__content-title">Latest trailers</h2>
            <ul class="trailers__content-list">
              <p
                href="#"
                class="trailers__content-links"
                @click="addLinksActiveFirst"
                :class="{ linksActive: linksActiveFirst }"
              >
                Online
              </p>
              <p
                class="trailers__content-links"
                @click="addLinksActiveSecond"
                :class="{ linksActive: linksActiveSecond }"
              >
                On TV
              </p>
              <p
                href="#"
                class="trailers__content-links"
                @click="addLinksActiveThird"
                :class="{ linksActive: linksActiveThird }"
              >
                For Rent
              </p>
              <p
                href="#"
                class="trailers__content-links"
                @click="addLinksActiveFour"
                :class="{ linksActive: linksActiveFour }"
              >
                In Theaters
              </p>
            </ul>
          </div>
          <transition-group tag="div">
            <div
              class="trailers__content-movies"
              v-if="linksActiveFirst == true"
            >
              <div
                class="trailers__movies-items"
                v-for="(item, index) in trailersArr"
                :key="index"
              >
                <img
                  class="bg-fon"
                  :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                  alt=""
                />

                <div class="trailers__content-icon">
                  <i class="fas fa-play"></i>
                </div>

                <h2 class="trailers__movies-title">{{ item.name }}</h2>
                <p class="trailers__movies-text">
                  Трейлер | ({{ item.first_air_date }})
                </p>
              </div>
            </div>
            <div
              class="trailers__content-movies"
              v-if="linksActiveSecond == true"
            >
              <div
                class="trailers__movies-items"
                v-for="(item, index) in trailersSecondArr"
                :key="index"
              >
                <img
                  class="bg-fon"
                  :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                  alt=""
                />

                <div class="trailers__content-icon">
                  <i class="fas fa-play"></i>
                </div>
                <h2 class="trailers__movies-title">
                  {{ item.original_title }}
                </h2>
                <p class="trailers__movies-text">
                  Трейлер | ({{ item.release_date }})
                </p>
              </div>
            </div>
            <div
              class="trailers__content-movies"
              v-if="linksActiveThird == true"
            >
              <div
                class="trailers__movies-items"
                v-for="(item, index) in trends"
                :key="index"
              >
                <img
                  class="bg-fon"
                  :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                  alt=""
                />

                <div class="trailers__content-icon">
                  <i class="fas fa-play"></i>
                </div>
                <h2 class="trailers__movies-title">
                  {{ item.original_title }}
                </h2>
                <p class="trailers__movies-text">
                  Трейлер | ({{ item.release_date }})
                </p>
              </div>
            </div>
            <div
              class="trailers__content-movies"
              v-if="linksActiveFour == true"
            >
              <div
                class="trailers__movies-items"
                v-for="(item, index) in trendsWeek"
                :key="index"
              >
                <img
                  class="bg-fon"
                  :src="`https://www.themoviedb.org/t/p/w220_and_h330_face/${item.poster_path}`"
                  alt=""
                />

                <div class="trailers__content-icon">
                  <i class="fas fa-play"></i>
                </div>
                Трейлер | ({{ item.release_date }})
                <h2 class="trailers__movies-title">
                  {{ item.original_title }}
                </h2>
                <p class="trailers__movies-text"></p>
              </div>
            </div>
          </transition-group>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Trailers",
  data() {
    return {
      trailersArr: [],
      trailerSecondArr: [],
      trends: [],
      trendsWeek: [],
      linksActiveFirst: true,
      linksActiveSecond: false,
      linksActiveThird: false,
      linksActiveFour: false,
      changeActive: true,
      newArr: [],
    };
  },
  methods: {
    spliceArr(arr) {
      arr.splice(-17);
    },
    spliceSecondArr(arr) {
      arr.splice(-13);
    },
    addLinksActiveFirst() {
      this.linksActiveFirst = true;
      this.linksActiveSecond = false;
      this.linksActiveThird = false;
      this.linksActiveFour = false;
    },
    addLinksActiveSecond() {
      this.linksActiveFirst = false;
      this.linksActiveSecond = true;
      this.linksActiveThird = false;
      this.linksActiveFour = false;
    },
    addLinksActiveThird() {
      this.linksActiveFirst = false;
      this.linksActiveSecond = false;
      this.linksActiveThird = true;
      this.linksActiveFour = false;
    },
    addLinksActiveFour() {
      this.linksActiveFirst = false;
      this.linksActiveSecond = false;
      this.linksActiveThird = false;
      this.linksActiveFour = true;
    },
    fetchTrailersFirst() {
      fetch(
        `https://api.themoviedb.org/3/tv/on_the_air?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US&page=1`
      )
        .then((response) => response.json())
        .then((data) => {
          this.trailersArr = data["results"];
          this.spliceArr(data["results"]);
          this.newArr.push(this.trailersArr.find((item) => item.id === 85552));

          console.log(this.newArr);
        });
    },
    fetchPostMovies() {
      fetch(
        ` https://api.themoviedb.org/3/movie/now_playing?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US&page=1`
      )
        .then((response) => response.json())
        .then((data) => {
          this.trailersSecondArr = data["results"];
          this.spliceSecondArr(data["results"]);
        });
    },
    fetchPostTrends() {
      fetch(
        `https://api.themoviedb.org/3/movie/upcoming?api_key=259c54c53e1db75ca5c5abe2e40a02d0&language=en-US&page=1`
      )
        .then((response) => response.json())
        .then((data) => {
          this.trends = data["results"];
          this.spliceArr(data["results"]);
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
    this.fetchTrailersFirst();
    this.fetchPostMovies();
    this.fetchPostTrends();
    this.fetchPostTrendsWeek();
  },
};
</script>

<style>
.trailers__content-block {
  padding-left: 40px;
  padding-top: 30px;
  background: rgba(61, 59, 59, 0.829);
  margin-top: -20px;
}

.trailers__content-head {
  display: flex;
  color: white;
  align-items: center;
}

.trailers__content-title {
  font-size: 1.5em;
  font-weight: 600;
  margin-right: 30px;
}

.trailers__content-list {
  display: flex;
  align-items: center;
  border: 1px solid rgb(30, 213, 169);
  border-radius: 30px;
}

.trailers__content-links {
  color: white;
  margin-left: 15px;
  margin-right: 15px;
  cursor: pointer;
}

.trailers__content-links.linksActive {
  margin-left: 0px;
  margin-right: 0px;
}

.linksActive {
  border-radius: 10px;
  padding-top: 5px;
  padding-bottom: 5px;
  color: rgb(3, 37, 65);
  background: rgb(30, 213, 169);
  padding-left: 15px;
  padding-right: 15px;
}
.trailers__content-movies {
  display: flex;
  align-items: center;
  overflow-y: hidden;
  margin-top: 25px;
}
.trailers__movies-items {
  text-align: center;
  margin-bottom: 20px;
  transition: all 0.3s ease-in;
  padding: 20px;
  color: white;
  position: relative;
}
.trailers__content-icon {
  position: absolute;
  top: 48%;
  left: 50%;
  transform: translateX(-50%);
  transform: translateY(-100%);
  font-size: 24px;
}
.trailers__movies-items:hover {
  transform: scale(1.02);
}
.trailers__movies-items:last-of-type {
  margin-right: 20px;
}

.bg-fon {
  opacity: 0.5;
  height: 280px;
}
</style>
