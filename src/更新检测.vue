<template>
  <div>
    <ul>
      <li v-for="(item, index) in arr" :key="index">{{ item }}</li>
    </ul>
    <button @click="reverseArr">数组翻转</button>
    <button @click="sliceArr">截取前3个</button>
    <button @click="updateBtn">更新第一个</button>
    <button @click.once="btn">新增一个</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [5, 3, 9, 2, 1],
    };
  },
  methods: {
    reverseArr() {
      this.arr.reverse();
    },
    sliceArr() {
      this.arr = this.arr.slice(0, 3);
    },
    updateBtn() {
      //   this.arr[0] = 1000;
      this.$set(this.arr, 0, 1000);
    },
    btn() {
      this.arr.splice(1, 0, "新来的");
    },
  },
};
</script>

<style>
</style>