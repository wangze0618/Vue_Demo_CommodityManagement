<template>
  <div>
    <p v-text="pn"></p>
    <p v-html="pn"></p>
    <p>{{ username }}</p>
    <label for="username">用户名</label>
    <input type="text" name="username" id="username" v-model="username" /><br />
    <label for="password">密码</label>
    <input type="password" name="password" id="password" v-model="password" />
    <br />

    <select name="select" id="" v-model="form">
      <option value="beijing">北京</option>
      <option value="shanghai">上海</option>
      <option value="chengdu">成都</option>
    </select>

    <br />
    男<input type="radio" name="gender" value="male" v-model="sex" /><br />
    女<input type="radio" name="gender" value="female" v-model="sex" />

    <input type="checkbox" value="11" v-model="num" />11
    <input type="checkbox" value="2" v-model="num" />2
    <input type="checkbox" value="3" v-model="num" />3
    <input type="checkbox" value="4" v-model="num" />4
  </div>
</template>

<script>
export default {
  data() {
    return {
      pn: "<span>hello</span>",
      username: "wangze",
      password: "www",
      form: "",
      sex: "male",
      num: [],
    };
  },
  methods: {},
};
</script>

<style>
</style>