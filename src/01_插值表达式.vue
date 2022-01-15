<template>
  <div>
    <h1>{{ msg }}</h1>
    <h2>{{ obj.name }}</h2>
    <h3>{{ obj.age >= 18 ? "已成年" : "未成年" }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "hello vue",
      obj: {
        name: "wangze",
        age: 21,
      },
    };
  },
};
</script>

<style>
</style>