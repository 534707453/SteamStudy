<template>
  <div id="app">
    <header>
      <Navbar />
      <div class="fullscreen-bg">
        <video loop muted autoplay playsinline
          poster="https://cdn.cloudflare.steamstatic.com/steam/clusters/frontpage/40c14a0bef16a5f75d7e1930/page_bg_schinese.jpg?t=1697739595"
          class="fullscreen-bg__video">
          <source src="./assets/Home/mp4_page_bg_schinese.mp4" type="video/webm">
          <source src="./assets/Home/mp4_page_bg_schinese.mp4" type="video/mp4">
        </video>
      </div>

      <div class="store_nav_area">
        <div class="store_nav">
          <ul>
            <li v-for="(store_nav_second, index) in nav_second" :key="index">
              <a href="#">{{ store_nav_second }}</a>
            </li>
          </ul>
          <div class="box">
            <div class="Search">
              <ul>
                <li>
                  <input class="nav_inp" type="search" v-model="searchText" @focus="handleFocus" @blur="handleBlur"
                    :style="{ color: isFocused ? 'white' : 'rgb(24, 58, 80)', fontStyle: isFocused ? 'normal' : 'italic' }">
                </li>
                <li><img width="26px" height="28px" src="./assets/nav/search_icon_btn.png" alt=""></li>
              </ul>
            </div>
          </div>
        </div>
      </div>

      <div class="mainBody">
        <p style="color: rgb(255, 255, 255); font-size: 14px; position: relative; top: 95px; left: 70px;">精选和推荐</p>
        <carousel></carousel>
      </div>
    </header>

  </div>
</template>
 
<script>

import Navbar from './components/Navbar'
import carousel from './components/carousel'
export default {
  name: 'app',
  components: {
    Navbar,
    carousel
  },
  data() {
    return {
      isFocused: false,
      searchText: '搜索',
      nav_second: ["您的商店", "新鲜推荐", "类别", "点数商店", "新闻", "实验室"]
    }
  },
  methods: {
    handleFocus() {
      this.isFocused = true;
      this.searchText = '';
    },
    handleBlur() {
      this.isFocused = false;
      if (this.searchText === '') {
        this.searchText = '搜索';
      }
    },
  }
}
</script>
 
<style  lang="css">
.mainBody {
  width: 100%;
  height: 900px;
  background: radial-gradient(circle 450px at 25% 0, rgb(24, 66, 82), rgb(26, 42, 59));
  margin-top: -8px;
  
}

.Search {
  position: relative;
  left: 292px;
}

.Search ul li {
  display: inline;
  list-style-type: none;
  padding: 0;
}

.Search ul li img {
  position: relative;
  top: 2px;
}

.Search input {
  background-color: rgb(49, 98, 130);

}


.Search ul {
  display: flex;
  align-items: center;
}

.nav_inp {
  padding: 6px 22px;
  border-radius: 3px;
  border: 0px;
  outline: none;
  width: 190px;
}

.store_nav_area {
  width: 940px;
  height: 66px;
  color: #E5E5E5;
  position: absolute;
  top: 105px;
  left: 296px;
}

.store_nav {
  width: 940px;
  height: 35px;
  margin-top: 29px;


  box-shadow: 5px 5px 3px -4px rgba(13, 13, 13, 0.8);
  display: flex;
  align-items: center;
  background: rgb(56, 97, 144);
  background: -webkit-linear-gradient(to right, rgb(56, 97, 144), rgb(24, 54, 124));
  background: linear-gradient(to right, rgb(56, 97, 144), rgb(24, 54, 124));
}

.store_nav li {
  list-style-type: none;
  padding: 0;
  display: inline;
}

.store_nav a {
  text-decoration: none;
  color: rgb(217, 217, 217);
  font-weight: inherit;
  font-size: 13px;
  font-weight: bold;
  padding: 3px 15px;
}

.fullscreen-bg__video {
  margin-left: 50%;
  transform: translateX(-50%);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}

header {
  background: rgb(23, 29, 37);
  width: auto;
  height: 104px;
}
</style>
