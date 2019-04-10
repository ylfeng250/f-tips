<template>
  <div id="app">
    <f-tips tip="上边提示" position="top">
      <a href="#">top</a>
    </f-tips>
    <f-tips tip="底部提示" position="bottom" background-color="blue">
      <a href="#">bottom</a>
    </f-tips>
    <f-tips tip="左边提示" position="left" font-size="30px">
      <a href="#">left</a>
    </f-tips>
    <f-tips tip="右边提示" position="right" font-color="red" font-size="20px">
      <a href="#">right</a>
    </f-tips>
  </div>
</template>

<script>
import FTips from './components/f-tips'

export default {
  name: 'App',
  components: {
    FTips
  }
}
</script>

<style>
#app {
  display: flex;
  justify-content: space-around;
  margin-top: 100px;
}
</style>
