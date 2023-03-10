<template>
  <div id="app">
    <ScaleImage :src="imgSrc" />
  </div>
</template>

<script>
import ScaleImage from './components/scale-image.vue'
export default {
  components: { ScaleImage },
  name: 'App',
  data() {
    return {
      imgSrc: 'http://101.43.51.163:3000/upload/94815ae581d1227f55e988a18ef2076636bf93.png',
    }
  },
}
</script>

<style>
#app {
  height: 200vh;
  position: relative;
}
.box {
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
