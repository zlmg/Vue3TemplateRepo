<script setup lang="ts">
import {computed, ref} from "vue";
import HelloWorldPage from "./pages/demo/HelloWorldPage.vue";
import NotFound from "./pages/demo/NotFound.vue";
import DemoIndex from "./pages/demo/index.vue"

const routes: { [key: string]: any} = {
  '/': HelloWorldPage,
  '/demo': DemoIndex,
}

debugger
const currentPath = ref(window.location.hash)
window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})
const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})

</script>

<template>
  <div class="menu">
    <a href="#/">Home</a>
    <a href="#/demo">Demo</a>
  </div>
  <component :is="currentView"></component>
</template>

<style scoped>
.menu {
  padding: 20px;
  /*width: 1000px;*/
  /*height: 100%;*/
  display: flex;
  gap: 20px;
}
</style>
