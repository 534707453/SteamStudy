<template>
  <div class="carousel">
    <!-- 轮播图内容 -->
    <img class="gameMainImg" src="" alt="">
    <div class="gameInfo">
      <div class="gameName"><h1 style="color: rgb(255, 255, 255);">使命召唤</h1></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'carousel'
}
</script>

<style lang="css">
.gameInfo{
  background-color: rgb(34, 254, 0);
  width: 314px;
  height: 353px;
  position: relative;
  left: 600px;
}

.gameMainImg{
  width: 616px;
  height: 100%;
  background: #c31b1b;
}
  .carousel{
    background: #ffffff;
    width: 940px;
    height: 353px;
    margin-top: 120px;
    margin-left: 320px;
  }
</style>
