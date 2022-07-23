<template>
  <div class="hello">
    <el-tooltip class="item1" effect="dark" content="请输入账号" placement="bottom">
      <el-input v-model="zhanghao" placeholder="账号"></el-input>
    </el-tooltip>
    <el-tooltip class="item" effect="dark" content="请输入密码" placement="bottom">
      <el-input placeholder="密码" v-model="message" show-password></el-input>
    </el-tooltip>
    <p>账号倒数： {{ reversedMessage }}</p>
    <div v-if="isshow">Vue is awesome!</div>
    <div v-for="(todo, index) in todos" v-bind:key="index">{{ index + 1 }}.{{ todo.text }}</div>
    <div>{{ fanz }}</div>
    <el-button v-on:click="reverserve" size="mini">😁反转一下</el-button>
    <el-badge :value="count" class="item">
      <el-button size="small" @click="returnAmsg">回复</el-button>
    </el-badge>
    <!-- <img :src="picture"> -->

  </div>
</template>

<script>
// import axios from 'axios'
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      count: null,
      message: '',
      zhanghao: '',
      city: '',
      isshow: true,
      todos: [{ text: 'hah' }, { text: 'lk' }, { text: 'wzdf' }],
      fanz: '上海自来水来自上海?',
      picture: 'https://img1.baidu.com/it/u=1966616150,2146512490&fm=253&fmt=auto&app=138&f=JPEG?w=751&h=500'
    };
  },
  mounted() {
    setTimeout(() => {
      this.isshow = false
    }, 3000)
    // this.print()
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
    reverserve() {
      this.$message({
        message: "你的小可爱在找你哦~",
        type: "success",
      });
      this.fanz = this.fanz.split('').reverse().join('')
      this.count = this.count ? this.count + 1 : 1;
    },
    returnAmsg() {
      setTimeout(() => {
        this.count = ''
      }, 2000)

    }
    //   async print() {
    //     const res = await axios.get('http://learn.api.futureruntime.com/')
    //     console.log(res)
    //     this.city = res.data.data.location;
    //   }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
