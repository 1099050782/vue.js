<template>
  <div id="app">
    <h2>-----------App内容：info对象的内容是否是响应式</h2>
    <h2>{{$store.state.info}}</h2>
    <button @click="updateInfo">修改信息</button>

    <h2>-----------App内容</h2>
    <h2>{{$store.state.counter}}</h2>
    <button @click="addition">+</button>
    <button @click="subtraction">-</button>
    <button @click="addCount(5)">+5</button>
    <button @click="addCount(10)">+10</button>
    <button @click="addStudent">添加学生</button>

    <h2>-----------App内容：getters相关信息</h2>
    <h2>{{$store.getters.porwerCounter}}</h2>
    <h2>{{$store.getters.more20stu}}</h2>
    <h2>{{$store.getters.more20stuLength}}</h2>
    <h2>{{$store.getters.moreAgeStu(22)}}</h2>

    <h2>-----------hello Vuex内容</h2>
    <hello-vuex/>
  </div>
</template>

<script>
import HelloVuex from "./components/HelloVuex";

export default {
  name: 'App',
  components: {
    HelloVuex
  },
  data() {
    return {
      message: 'halou'
    }
  },
  methods: {
    addition() {
      //commit 提交方法
      this.$store.commit('increment')
    },
    subtraction() {
      this.$store.commit('decrement')
    },
    addCount(count) {
      //负载payload
      // //1.普通的提交封装
      // this.$store.commit('incrementCount', count)
      //2.特殊的提封装
      this.$store.commit({
        type: 'incrementCount',
        //提交时为对象
        count
      })
    },
    addStudent() {
      const stu = {id: 114, name: 'yangqi', age: 30}
      this.$store.commit('addStudent', stu)
    },
    updateInfo() {
      // this.$store.commit('updateInfo')
      this.$store
        .dispatch('aUpdateInfo', '携带信息')
        .then(res => {
        console.log('完成了提交');
        console.log(res);
      })
    }
  }
}
</script>

<style>

</style>
