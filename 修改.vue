<template>
  <div>
    <div v-if="hello">
      <!--3.使用-->
      <div
        v-if="!childLoad"
        style="height: 84px"
        v-loading="!childLoad"
        element-loading-text="拼命加载中"
        element-loading-spinner="el-icon-loading"
        element-loading-background="rgba(0, 0, 0, 0.8)"
      ></div>
      <HelloWorld
        v-if="childLoad"
        :msg="asyncMsg"
        v-bind:cakeName="asyncMsg"
      ></HelloWorld>
      <hello-world msg="曲项向天歌"></hello-world>
    </div>
  </div>
</template>

<script>
// 1.把你的组件引入
import HelloWorld from "./components/HelloWorld.vue";
export default {
  // 2.再components属性上添加子组件
  components: {
    HelloWorld,
  },
  name: "App",
  data: function () {
    return {
      hello: true,
      child: true,
      asyncMsg: "",
      childLoad: false,
    };
  },
  methods: {
    async sleep(time) {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve();
        }, time);
      });
    },
  },
  mounted() {
    setTimeout(async () => {
      // this.false;
      console.log("执行完了，有结果不");
      this.asyncMsg = "老大爷";
      this.childLoad = true;

      // 等一会儿吧
      await this.sleep(3000);
      this.childLoad = false;
      // this.$nextTick(() => this.childLoad = false)
      // 异步任务
      setTimeout(() => {
        // this.false;
        console.log("执行完了，有结果不");
        this.asyncMsg = "精神小伙";
        this.childLoad = true;
      }, 3000);
    }, 3000);
    // setInterval(() => this.child = !this.child, 2000)
  },
};
</script>
