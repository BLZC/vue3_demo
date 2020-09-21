<template>
  <div id="hello">{{count}}-{{myObj.name}}</div>
</template>

<script>
import { ref, reactive, onUnmounted, onMounted, onUpdated, watchEffect, toRefs, inject } from 'vue'

export default {
  props: {
    data: {
      type: Object
    }
  },
  setup (props, context) {
    const count = ref(0)
    const myObj = reactive({ name: 'lzc', age: 12 })

    const fn = () => {
      return 123
    }

    const { show, title } = toRefs(props.data)

    const testInject = inject('parentName', 'chil')
    watchEffect(() => {
      console.log(show.value)
    })

    onMounted (() => {
      const ele = document.getElementById('hello')
      console.log(testInject)
    })

    onUpdated (() => {
      console.log(show.value)
    })

    onUnmounted (() => {
    })
    return {
      count,
      myObj,
      fn
    }
  }
}
</script>
