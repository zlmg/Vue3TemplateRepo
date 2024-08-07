<script setup lang="ts">
import {useDark, useLocalStorage, useMouse, usePreferredDark, useToggle} from "@vueuse/core"

//  跟踪鼠标位置
const { x, y } = useMouse()

// // 用户是否喜欢暗黑主题
// const isDark = useDark()
//
// const toggleDark = useToggle(isDark)

// 在本地存储中持久化状态
const store = useLocalStorage("my-store", {
  name: "Apple",
  color: 'red'
})

</script>

<template>
  <div class="demo-list">
    <div class="demo-item">
      <span>useMouse:</span>
      <div>
        <p>x: {{ x }}</p>
        <p>y: {{ y }}</p>
      </div>
    </div>
<!--    <div class="demo-item">-->
<!--      <span>isDark: {{ isDark }}</span>-->
<!--      <el-switch v-model="isDark"/>-->
<!--      <button @click="toggleDark">Toggle Dark</button>-->
<!--    </div>-->
  </div>
</template>

<style scoped>
.demo-list {
  display: flex;
  gap: 20px;
  .demo-item {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
