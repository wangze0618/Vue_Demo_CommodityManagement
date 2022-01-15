<template>
  <div>
    <span>全选：</span>
    <input type="checkbox" v-model="isAll" />
    <button @click="reverseSelection()">反选</button>

    <ul>
      <li v-for="(item,index) in arr" :key="index">
        <input type="checkbox" v-model="item.isChecked" />
        <span>{{ item.name }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [
        {
          name: "猪八戒",
          isChecked: false,
        },
        {
          name: "孙悟空",
          isChecked: false,
        },
        {
          name: "唐僧",
          isChecked: false,
        },
        {
          name: "白龙马",
          isChecked: false,
        },]
    }
  },
  methods: {
    reverseSelection() {
      this.arr.forEach(e => e.isChecked = !e.isChecked)
    }
  },
  computed: {
    isAll: {
      set(value) {
        this.arr.forEach(e =>
          e.isChecked = value
        );
      },
      get() {
        return this.arr.every(f => f.isChecked === true)
      }
    }
  }
}
</script>

<style>
</style>