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
    <hr />
    <button @click="showText = !showText">switch</button>
    <p
      v-if="showText"
      :style="{
        color: 'red',
      }"
    >
      Hello,World!
    </p>
    <p v-else>哈喽，世界!</p>
    <hr />
    <test-hook @hook:updated="handleUpdate"></test-hook>
  </div>
</template>

<script>
import gsap from "gsap";
import Counter from "./Counter.vue";
import TestHook from "./TestHook.vue";
export default {
  name: "App",
  components: {
    Counter,
    TestHook,
  },
  data() {
    return {
      show: false,
      count: 0,
      showNumber: 0,
      showText: true,
    };
  },
  methods: {
    handleUpdate() {
      alert("I had updated");
    },
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
