<template>
  <ul>
    <li>father页面</li>
    <li>来自于grandfather的消息：{{msg}}</li>
    <li>修改来自于father的消息：<input type="text" v-model="fromFatherMsg"><button @click="callback">回传</button></li>
    <li>
      <button @click="emitToMother">传递消息给mother</button>
    </li>
  </ul>
</template>

<script>
import store from '@/util/store'
export default {
  name: 'father',
  props: ['msg'],
  computed: {
    fromFatherMsg: {
      get () {
        return this.msg
      },
      set (v) {
        this.$emit('update:msg', v)
      }
    }
  },
  methods: {
    callback () {
      this.$emit('update:msg', '来自于father的修改')
    },
    emitToMother () {
      store.$emit('toMother', '来自于father的消息')
    }
  }
}
</script>

<style scoped>

</style>
