<template>
  <div>            
             <!-- //love是子组件传来的参数，ICanSeeYou是父组件用来接受的参数//answer是父组件向子组件传入的参数 -->
    <FirstComponet @love="ICanSeeYou" :answer="fatherinfo"></FirstComponet>
    <div v-if="true">
      <!-- <HelloWorld v-if="childLoading" :msg="ppx"></HelloWorld> -->
      <HelloWorld :msg="info"></HelloWorld>
      <!-- 父组件用自身info变量（也可以是字符串）给子组件传入名为msg参数 -->
      <!--（ ：）用于给标签绑上变量 -->
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import FirstComponet from './components/FirstComponet.vue';
export default {
  components: {
    HelloWorld: HelloWorld,
    FirstComponet
  },

  name: "App",
  data: function () {       //data的函数式
    return {
      fatherinfo: null,     //定义一个空变量来存放子组件传来的值
      hello: true,
      ppx: '',
      childLoading: false,
      info:"唯见江心秋月白"
    }
  },
  methods: {  
    ICanSeeYou(childinfo) {
      console.log('icanseeyou', childinfo)
      this.fatherinfo = childinfo;            //用一个父组件里一个变量来接收子组件传来的值
      this.fatherinfo.color++;
    }
  },
  mounted() {
    // setTimeout(() => {
    //   console.log('结果');
    //   this.ppx = "琵琶行";
    //   this.childLoading = true;
    //   // setTimeout(() => {
    //   //   console.log('结果');
    //   //   this.ppx = "girl";
    //   //   // this.childLoading = true;

    //   // }, 3000)

    // }, 3000)             //父级传的参数是要等3秒才过去，所以有个异步问题
  }

};
</script>
