/* eslint-disable vue/no-parsing-error */
<template>
  <div>
    <ul>
      <li v-for="(item, index) in arr" :key="index">
        {{ item }}
        <a href="#" @click="deleteo(index)" :data="index">删除</a>
      </li>
    </ul>
    <button @click.stop="add()">生成</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [1, 5, 3],
    };
  },
  methods: {
    add() {
      this.arr.push(parseFloat((Math.random() * 10).toFixed(0)));
    },
    deleteo(index) {
      this.arr.splice(index, 1);
      console.log(this.arr);
    },
  },
};
</script>

<style>
</style>