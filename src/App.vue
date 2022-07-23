<template>
  <div>
    <div v-if="hello">
      <HelloWorld></HelloWorld>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
export default {
  components: {
    HelloWorld,
  },
  name: "App",
  data: function() {
    return {
      hello: true,
  
      
    }
  },
  // mounted() {
  //   setTimeout(() => this.hello = false, 3000)
  // }
};
</script>
