<script setup lang="ts">
import { capitalize } from './helpers.ts'
const [modelValue, modelModifiers] = defineModel({
  // get() omitted as it is not needed here
  set(value) {
    // if the .trim modifier is used, return trimmed value
    if (modelModifiers.trim) {
      return value.trim()
    }
    // otherwise, return the value as-is
    return value
  }
})


import { mergeProps } from 'vue'

const handlerA = () => {
  console.log('handlerA')
}

const handlerB = () => {
  console.log('handlerB')
}

const one = {
  class: 'foo',
  onClick: handlerA
}

const two = {
  class: { bar: true },
  onClick: handlerB
}

const merged = mergeProps(one, two)
console.log(merged)
/**
 {
 class: 'foo bar',
 onClick: [handlerA, handlerB]
 }
 */
</script>

<template>
  <div>{{ capitalize('hello world') }}</div>
</template>

<style scoped>

</style>
