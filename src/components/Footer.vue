<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__content">
        <div class="footer__content-block">
          <div class="footer__content-items">
            <div class="footer__content-logo">
              <img
                src="https://www.themoviedb.org/assets/2/v4/logos/v2/blue_square_2-d537fb228cf3ded904ef09b136fe3fec72548ebc1fea3fbbd1ad9e36364db38b.svg"
                alt=""
              />
              <div class="footer__content-btn">
                <a href="#!">Join the Community</a>
              </div>
            </div>
          </div>
          <div class="footer__content-items">
            <ul class="footer__content-list">
              <h2 class="footer__content-title">The Basics</h2>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">About TMDB</a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Contact Us</a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Support Forums</a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">API</a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">System Status</a>
              </li>
            </ul>
          </div>
          <div class="footer__content-items">
            <ul class="footer__content-list">
              <h2 class="footer__content-title">Get Involved</h2>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link"
                  >Contribution Bible
                </a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Add New Movie </a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Add New TV Show</a>
              </li>
            </ul>
          </div>

          <div class="footer__content-items">
            <ul class="footer__content-list">
              <h2 class="footer__content-title">Community</h2>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Guidelines</a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Discussions </a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Leaderboard</a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Twitter </a>
              </li>
            </ul>
          </div>
          <div class="footer__content-items">
            <ul class="footer__content-list">
              <h2 class="footer__content-title">LEGAL</h2>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Terms of Use </a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">API Terms of Use </a>
              </li>
              <li class="footer__content-li">
                <a href="#!" class="footer__content-link">Privacy Policy </a>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style>
.footer {
  background: #031d33;
  padding-top: 50px;
  padding-bottom: 50px;
}
.footer__content-logo img {
  width: 130px;
  height: 94px;
  margin-left: 120px;
}
.footer__content-logo {
  display: flex;
  flex-direction: column;
}
.footer__content-logo a {
  margin-top: 25px;
  font-weight: bold;
  display: inline-block;
  word-wrap: break-word;
  white-space: normal;
  text-transform: uppercase;
  border-color: #fff;
  background-color: #fff;
  color: rgba(1, 180, 228);
  font-size: 1.1em;
  padding: 8px 16px;
  border: 2px solid #fff;
  border-radius: 5px;
}
.footer__content-block {
  display: flex;
  justify-content: space-between;
}
.footer__content-li {
  margin-top: 8px;
}
.footer__content-link {
  color: white;
  transition: all 0.5s;
}
.footer__content-link:hover {
  color: rgb(156, 137, 137);
}
.footer__content-title {
  color: white;
  font-weight: bold;
  font-size: 1.2em;
  line-height: 1.4em;
  text-transform: uppercase;
  white-space: nowrap;
  margin-top: 50px;
}
</style>
