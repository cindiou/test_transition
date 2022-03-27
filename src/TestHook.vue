<template>
  <div>
    <h1>测试hook:{{ count }}</h1>
    <button @click="count++">+1</button>
    <button @click="count--">-1</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  methods: {},
};
</script>