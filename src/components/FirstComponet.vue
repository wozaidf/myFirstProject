<template>
    <div>
        <el-button v-on:click="DoYouSeeMe">😁点我一下看能不能看到父亲</el-button>
        {{ formatAns || '没回答我' }}
    </div>
</template>

<script>


export default {
    name: 'FirstComponet',
    props: ['answer'],
    data: function () {
        return {
            count: 0,
            // nameq:''
        }
    },
    methods: {
        DoYouSeeMe() {
            this.$emit('love', { color: this.count + 1 })
        }
    },
    watch:{
        answer:function(current,old){
            this.count=current.color
            // console.log(current,old)
        }
    },
    // mounted() {
    //     this.nameq=this.answer?.color
    //     this.count=this.nameq
    // },                                           //错误想法
    computed: {
        formatAns: function () {
            return this.answer && this.answer.color
        }
    }
}



</script>



<style scoped>
</style>