<template>
  <div>    
    <group title="cell demo" ref='mytitle'>
      <cell title="two" value="Cool" is-link @click.native="change"></cell>
      <cell title="two2" :value="msg" is-link :link="{path: 'one'}"></cell>
    </group>
  </div>
</template>

<script>
import { Group, Cell,Alert } from 'vux'

export default {
  components: {
    Group,
    Cell,
    Alert
  },
  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'Hello World!'
    }
  },
  methods:{
      change(){
          this.msg = 'im ok'
          // 显示
        this.$vux.alert.show({
        title: '提示',
        content: '确认操作?',
        onShow () {
            console.log('Plugin: I\'m showing')
        },
        onHide () {
            console.log('Plugin: I\'m hiding')
        }
        })
      }
  },
  created(){
    this.msg = 'first in'
    //vue.$refs.mytitle.title = 'Init'
  }
}
</script>

<style>
.vux-demo {
  text-align: left;
}
.logo {
  width: 100px;
  height: 100px
}
</style>
