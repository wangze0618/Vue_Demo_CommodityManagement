<template>
  <div>
    <!-- <a :href="location" target="_blank" @click.prevent="stop">百度</a>
    <a :href="location" target="_blank" @click="stopTwo(5, $event)">百度</a> -->
    <!-- <img :src="iconURL" alt="" /> -->
    <!-- <p>你要购买的数量：{{ count }}</p>
    <button @click="count = count + 1">+1</button>
    <button @click="add()">+1</button>
    <button @click="second()">减少</button>
    <button @click="addFive(3)">一次加3件</button>

    <div @click="son()">
      <p @click.stop="logP()">hello</p>
    </div>
    <form action="" method="get" @submit.prevent="stop()">
      <input type="text" name="" id="" />nihao1
      <input type="submit" value="ss" />
    </form> -->
    <h1>{{ str }}</h1>
    <button @click.once="transStr()">trans</button>
  </div>
</template>

<script>
// 导入本地图片需要 import导入
// import iconURL from "./assets/backiee-139987.jpg";
export default {
  data() {
    return {
      location: "http://www.baidu.com",
      // iconURL: iconURL,
      count: 0,
      str: "Hello,World",
    };
  },
  methods: {
    transStr() {
      // let arr = [];
      // let arr = this.str.split("");
      // for (let index = 0; index < this.str.length; index++) {
      //   arr[arr.length] = this.str[index];
      // }
      // this.str = arr.reverse().join("");

      this.str = this.str.split("").reverse().join("");
    },
    // stop() {
    //   console.log(111);
    // },
    // stopTwo(num, e) {
    //   e.preventDefault();
    // },
    // add() {
    //   this.count++;
    // },
    // second() {
    //   if (this.count <= 0) {
    //     alert("stop!");
    //   } else {
    //     this.count--;
    //   }
    // },
    // addFive(num) {
    //   this.count = this.count + num;
    // },
  },
};
</script>

<style scoped>
.red {
  color: red;
}
.black {
  color: blue;
}
a {
  text-decoration: none;
  color: #000;
}
</style>