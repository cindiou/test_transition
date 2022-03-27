<template>
  <div id="app">
    <Counter :level="1"></Counter>
    <h1>添加了新的内容</h1>
    <input type="number" v-model="count" step="10" />
    <p>数字：{{ dealNumber }}</p>
    <button @click="show = !show">切换</button>
    <transition
      enter-active-class="animate__animated animate__tada"
      leave-active-class="animate__animated animate__backInDown"
    >
      <h1 v-if="show">Hello,World</h1>
    </transition>
  </div>
</template>

<script>
import gsap from "gsap";
import Counter from "./Counter.vue";
export default {
  name: "App",
  components: {
    Counter,
  },
  data() {
    return {
      show: false,
      count: 0,
      showNumber: 0,
    };
  },
  computed: {
    dealNumber() {
      return this.showNumber.toFixed(0);
    },
  },
  watch: {
    count(newValue) {
      gsap.to(this, { duration: 1, showNumber: newValue });
    },
  },
};
</script>

<style>
.animate__backInDown {
  animation-direction: reverse;
}
</style>
