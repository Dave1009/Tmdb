<template>
  <div class="header__content">
    <div class="container">
      <div class="header__content-block">
        <div class="header__content-item">
          <h1 class="header__content-title">2021</h1>
          <h2 class="header__content-text">That's a Wrap</h2>
          <h3>
            <a href="#!" class="header__content-link"
              >Let's dive into 2021's best and worst! →</a
            >
          </h3>
        </div>
        <div class="header__content-form">
          <input
            class="header__content-input"
            placeholder="Search for a movie, tv show, person......"
            value=""
          />
          <input type="submit" value="Search" class="header__content-submit" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.header__content-item {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;
  padding-top: 50px;
}

.header__content-block {
  background: url("https://www.themoviedb.org/assets/2/v4/taw/2021/shape_8-fae706ec0da1ef4e0c48b6abfe1984cfb5808be9dfc01619b25b2a9691c43f56.svg")
    50% 50% no-repeat;
  height: auto;
  max-height: none;
  margin-bottom: 20px;
}

.header__content-title,
.header__content-text {
  text-align: center;
}

.header__content-title {
  font-size: 8em;
  width: 100%;
  color: white;
  font-family: "Mono";
}

.header__content-text {
  font-family: "Source Sans Pro", Arial, sans-serif;
  width: 100%;
  font-size: 2.8em;
  color: white;
}

.header__content-link {
  color: white;
  font-weight: 600;
  width: 100%;
  font-size: 1.8em;
  text-align: center;
  margin-bottom: 40px;
  padding-bottom: 10px;
  margin-top: 5px;
}

.header__content-link:hover {
  border-bottom: 2px solid rgb(240, 179, 122);
}

.header__content-form {
  display: flex;
  justify-content: space-between;
  width: 100%;
  height: 36px;
  line-height: 36px;
  font-size: 1.1em;
  color: rgba(0, 0, 0, 0.5);
  border: none;
  border-radius: 30px;
  padding: 10px 20px;
  border: 2px solid rgba(255, 202, 154);
  position: relative;
  top: 60px;
  left: 0;
}

.header__content-input {
  width: 100%;
  height: 100%;
  outline: none;
}

.header__content-submit {
  padding: 10px 26px;
  background: white;
  border-radius: 30px;
  position: absolute;
  top: 0;
  right: 0;
  z-index: 9999;
  cursor: pointer;
}
</style>
