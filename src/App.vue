<template>
  <demo
    v-if="isRouterAlive"
    :svgColor="svgColor"
    :src="src"
    :width="'450px'"
    :height="'450px'"
    @result="resultColor"
  ></demo>
</template>

<script>
import { ref, nextTick, provide } from 'vue'
import Demo from './Demo.vue'
import testsvg from './test.svg'
export default {
  name: 'App',
  components: {
    Demo
  },
  setup() {
    const svgColor = ref('#0C5DB0')
    const src = ref(testsvg)
    // 局部组件刷新
    const isRouterAlive = ref(true)
    const reload = () => {
      isRouterAlive.value = false
      nextTick(() => {
        isRouterAlive.value = true
      })
    }
    provide('reload', reload)
    const resultColor = (returnData) => {
      svgColor.value = returnData
    }
    return { svgColor, src, isRouterAlive, resultColor }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  /* 设置body高度为100%窗口高度 */
  height: 100vh;
  /* 弹性盒子布局 水平垂直居中 文字居中 */
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background: linear-gradient(200deg, #a8edea, #fed6e3);
}
</style>
