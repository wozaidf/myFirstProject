<template>
  <div>
    <FirstComponet @love="ICanSeeYou" :answer="fatherinfo"></FirstComponet>
    <div v-if="false">
      <HelloWorld v-if="childLoading" :msg="ppx"></HelloWorld>
      <HelloWorld msg="唯见江心秋月白"></HelloWorld>
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
  data: function () {
    return {
      fatherinfo: null,
      hello: true,
      ppx: '',
      childLoading: false
    }
  },
  methods: {  

    
    ICanSeeYou(childinfo) {
      console.log('wcanseeyou', childinfo)
      this.fatherinfo = childinfo;
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
