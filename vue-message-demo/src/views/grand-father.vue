<template>
  <div style="border: 1px solid #eeee; background-color: beige">
    <ul class="home">
      <li>grandfather页面</li>
      <li>传递给father的消息：{{tofather}}</li>
      <li>
        传递给mother的消息：{{toMother}}
      </li>
      <button @click="click">点击</button>
    </ul>
    <div style="display: flex;flex-direction: row;">
      <father style="background-color: darkkhaki;height:auto;flex:1" :msg.sync="tofather"></father>
      <mother style="background-color: darkgray;height:auto;flex:1"  :msg="toMother"></mother>
    </div>
  </div>
</template>

<script>
import father from '@/views/father'
import Mother from './mother'

export default {
  name: 'Home',
  components: {
    Mother,
    father
  },
  data () {
    return {
      tofather: '',
      toMother: null
    }
  },
  methods: {
    click () {
      this.tofather = '来自于grandfather'
      this.toMother = [
        {
          id: '1',
          type: '水果',
          value: [
            {
              name: '芒果',
              value: 30
            },
            {
              name: '葡萄',
              value: 10
            }
          ]
        },
        {
          id: '1',
          type: '蛋糕',
          value: [
            {
              name: '提拉米苏',
              value: '100¥'
            },
            {
              name: '戚风',
              value: '50¥'
            }
          ]
        }
      ]
    }
  }
}
</script>
<style>
  ul{
    list-style: none;
    display: flex;
    flex-direction: column;
  }
  li{
    text-align: left;
    margin: 10px;
  }
  li:first-child{
    width: 200px;
    font-weight: 500;
    margin: 10px 0;
    font-size: 20px;
  }
  button{
    width: 100px;
  }

</style>
