<template>
  <div class="test">
    <h1>test page</h1>
    <h2>{{count.old}}</h2>
    <h2>{{doubleCount}}</h2>
    <button @click="add">点击</button>
  </div>
</template>

<script>
import { ref, watch, computed, getCurrentInstance } from 'vue'
export default {
  setup () {
    const count = ref({ name: 'zhouhao', old: 22 })
    const add = () => {
      count.value.old++
    }
    watch(() => count.value.old, val => {
      console.log('old被更新了,被改成了：', val)
    })
    const doubleCount = computed(() => count.value.old * 100)
    return {
      count, add, doubleCount
    }
  }
}
</script>

<style scoped>
.test {
  color: red;
}
</style>
