<template>
  <HelloWorld ref="root" :data="detailData"/>
  <button @click="() => { detailData.show = true }">新增</button>
  <button @click="() => { detailData.show = false }">关闭</button>
</template>

<script>
import { ref, reactive, onMounted, provide } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup () {
    const root = ref(null)
    const detailData = reactive({
      name: '',
      show: false,
      title: '新增',
      obj: {}
    })
    const open = () => {
      detailData.show = true
    }

    provide('parentName', 'root')
    onMounted(() => {
    })

    return {
      root,
      detailData,
      open
    }
  }
}
</script>
