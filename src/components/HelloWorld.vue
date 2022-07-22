<template>
  <div class="hello">
    <el-tooltip class="item1" effect="dark" content="请输入账号" placement="bottom">
      <el-input v-model="zhanghao" placeholder="账号"></el-input>
    </el-tooltip>
    <el-tooltip class="item" effect="dark" content="请输入密码" placement="bottom">
      <el-input placeholder="密码" v-model="message" show-password></el-input>
    </el-tooltip>
    <p>账号倒数： {{ reversedMessage }}</p>
    <div>城市:{{ city }}</div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      message: '',
      zhanghao: '',
      city: ''
    };
  },
  mounted() {
    this.print()
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.zhanghao.split('').reverse().join('')
    }
  },
  zhanghao: function (current, old) {
    console.log('这是当前值', current)
    console.log('这是旧的值', old)
  },
  methods: {
    async print() {
      const res = await axios.get('http://learn.api.futureruntime.com/')
      console.log(res)
      this.city = res.data.data.location;
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
