<template>
  <div>
    <!-- <ul>
      <li v-for="(item, index) in arr" :key="index">
        {{ index }} -- {{ item }}
      </li>
    </ul> -->

    <!-- <ul>
      <li v-for="item in stuArr" :key="item.id">
        <span>ID:{{ item.id }}</span
        ><br />
        <span>name:{{ item.name }}</span
        ><br />
        <span>sex:{{ item.sex }}</span
        ><br />
        <span>hobby:{{ item.hobby }}</span
        ><br />
      </li>
    </ul> -->
    <!-- 
    <ul>
      <li v-for="(item, index) in tObj" :key="index">
        {{ index }} -- {{ item }}
      </li>
    </ul> -->

    <h1 v-show="count">hello world</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: ["小明", "小欢欢", "大黄"],
      stuArr: [
        {
          id: 1001,
          name: "孙悟空",
          sex: "男",
          hobby: "吃桃子",
        },
        {
          id: 1002,
          name: "猪八戒",
          sex: "男",
          hobby: "背媳妇",
        },
      ],
      tObj: {
        name: "小黑",
        age: 18,
        class: "1期",
      },
      count: 10,
    };
  },
};
</script>

<style>
</style>