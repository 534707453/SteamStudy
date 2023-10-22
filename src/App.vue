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
          
        </div>
      </div>
    </header>
  </div>
</template>
 
<script>
import Navbar from './components/Navbar'
export default {
  name: 'app',
  components: {
    Navbar
  }
}
</script>
 
<style  lang="css">
.store_nav_area {
  background: #444343;
  width: 940px;
  height: 66px;
  color: #E5E5E5;
  position: absolute;
  top: 104px;
  left: 292px;
}

.store_nav{
  width: 940px;
  height: 33px;
  margin-top: 27px;
  background-color: #E5E5E5;
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
}</style>
