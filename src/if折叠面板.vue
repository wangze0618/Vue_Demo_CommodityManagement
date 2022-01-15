<template>
  <div>
    <div id="root">
      <h1>折叠面板</h1>

      <div id="header">
        <p>芙蓉楼送人</p>
        <!-- <span @click="changeShow" v-if="showState">收起</span> -->
        <!-- <span @click="changeShow" v-else>展开</span> -->
        <span @click="changeShow">{{ showState ? "收起" : "展开" }}</span>
      </div>

      <div id="content" v-show="showState">
        <p>寒雨连江夜入吴，</p>
        <p>平明送客楚山孤。</p>
        <p>洛阳亲友如相同，</p>
        <p>一片冰心在玉壶。</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showState: true,
    };
  },
  methods: {
    changeShow() {
      this.showState = !this.showState;
    },
  },
};
</script>
 
<style lang='less'>
a {
  text-decoration: none;
}
span {
  user-select: none;
  cursor: pointer;
}
#root {
  /* padding: 20px; */
  border: 1px solid #000;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 500px;
  margin: 0 auto;
}
#header {
  border: 1px solid #000;
  width: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
</style>