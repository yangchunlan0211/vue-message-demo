<template>
  <ul>
    <li>mother页面</li>
    <li>来自于grandfather的消息：{{msg}}</li>
    <li>来自于father的消息：{{fromFather}}</li>
    <button @click="callback">回传</button>
  </ul>
</template>

<script>
import store from '@/util/store'
export default {
  name: 'mother',
  props: ['msg'],
  data () {
    return {
      fromFather: ''
    }
  },
  created () {
    const self = this
    store.$on('toMother', function (msg) {
      self.fromFather = msg
    })
  },
  methods: {
    callback () {
      this.msg[1].type = '好吃的蛋糕'
    }
  }
}
</script>

<style scoped>

</style>
