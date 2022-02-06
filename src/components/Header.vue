<template>
  <header class="header">
    <div class="header__nav-content">
      <div class="container">
        <nav class="header__nav">
          <div class="header__nav-logo">
            <router-link to="/">
              <img src="@/assets/img/logo.png" alt="TMDB" />
            </router-link>
            <ul class="header__nav-list">
              <p class="header__nav-links">Movies</p>
              <p class="header__nav-links">TV Shows</p>
              <p class="header__nav-links">People</p>
              <p class="header__nav-links">More</p>
            </ul>
          </div>
          <ul class="header__nav-list">
            <li><i class="fas fa-plus header__nav-links"></i></li>
            <li>
              <a href="#!" class="header__nav-links"> <span>EN</span></a>
            </li>
            <li><a href="#!" class="header__nav-links">Login</a></li>
            <li>
              <a
                href="https://www.themoviedb.org/signup"
                class="header__nav-links"
              >
                Join TMDB</a
              >
            </li>
            <li>
              <a href="#!"><i class="fas fa-search header__nav-links"></i></a>
            </li>
          </ul>
        </nav>
      </div>
    </div>
    <Content />
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  height: 100%;
}

/* Header Nav */
.header__nav-content {
  background: rgb(3, 37, 65);
}
.header__nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 64px;
}

.header__nav-logo {
  display: flex;
}

.header__nav-logo img {
  width: 154px;
  height: 20px;
}

.header__nav-list {
  display: flex;
  margin-left: 20px;
}

.header__nav-links {
  margin-left: 30px;
  color: white;
  cursor: pointer;
  transition: all 0.5s;
}
.header__nav-links:hover {
  color: rgba(255, 255, 255, 0.637);
}
.header__nav-links span {
  border: 1px solid white;
  padding: 3px;
  font-size: 12px;
  border-radius: 3px;
}
</style>
