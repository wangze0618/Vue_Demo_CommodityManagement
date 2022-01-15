<template>
  <div>
    <div class="container">
      <!-- 顶部框模块 -->
      <div class="row justify-content-center">
        <div class="col col-xl-8">
          <div class="form-group">
            <div class="input-group">
              <h4>品牌管理</h4>
            </div>
          </div>

          <!-- 数据表格 -->
          <table class="table table-bordered table-hover mt-2">
            <thead>
              <tr>
                <th>编号</th>
                <th>资产名称</th>
                <th>价格</th>
                <th>创建时间</th>
                <th>操作</th>
              </tr>
            </thead>
            <tbody>
              <tr style="text-align: center" v-for="(item,index) in list" :key="item.id">
                <td>{{ item.id }}</td>
                <td>{{ item.name }}</td>
                <!-- 如果价格超过100，就有red这个类 -->
                <td :class="{ red: item.price > 100 }">￥{{ item.price }}</td>
                <td>{{ item.time | timeFormat }}</td>
                <td>
                  <a href="#" @click.stop="deleteItem(index)">删除</a>
                </td>
              </tr>
              <tr v-show="(!this.list.length == 0)">
                <td>统计：</td>
                <td colspan="2">总价为：￥{{ totalPrice }}</td>
                <td colspan="2">平均价为：￥{{ avgPrice }}</td>
              </tr>
            </tbody>

            <tfoot v-show="(this.list.length == 0)">
              <tr>
                <td colspan="5" style="text-align: center">暂无数据</td>
              </tr>
            </tfoot>
          </table>

          <!-- 添加资产 -->
          <form class="form-inline form-flex">
            <div class="form-group">
              <div class="input-group">
                <input type="text" v-model="name" class="form-control" placeholder="资产名称" />
              </div>
            </div>&nbsp;&nbsp;&nbsp;&nbsp;
            <div class="form-group">
              <div class="input-group">
                <input type="text" v-model.number="price" class="form-control" placeholder="价格" />
              </div>
            </div>&nbsp;&nbsp;&nbsp;&nbsp;
            <!-- 阻止表单提交 -->
            <button class="btn btn-primary" @click.prevent="addList(); clear()">添加</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  data() {
    return {
      name: "", // 资产名称
      price: "", // 价格
      bool: false,
      list:
        // 从 localStorage里取出数据,如果没有值就默认为[], 有的话就是本身值
        JSON.parse(localStorage.getItem('pList')) ? JSON.parse(localStorage.getItem('pList')) : [],
    };
  },
  methods: {
    deleteItem(index) {
      // 删除商品
      this.list.splice(index, 1);
    },
    addList() {
      // 增加商品
      let id = this.list.length > 0 ? this.list[this.list.length - 1].id + 1
        : 100
      if (this.name.trim().length === 0 || this.price === 0) {
        alert('请输入正确的名称和价格！')
      } else {
        this.list.push({
          id: id,
          name: this.name,
          price: this.price,
          time: new Date()
        })
      }
    },
    clear() {
      this.name = ''
      this.price = ''
    }
  },
  filters: {
    timeFormat(value) {
      // 利用 moment第三方包 来处理时间
      return moment(value).format('YYYY-MM-DD')
    }
    // timeForm(value) {
    //   const year = value.getFullYear();
    //   const month = value.getMonth() + 1;
    //   const day = value.getDate();

    //   function data(t) {
    //     return t > 9 ? t : '0' + t
    //   }
    //   return `${year}-${data(month)}-${data(day)}`
    // }
  },
  computed: {
    totalPrice() {
      let price = 0;
      this.list.forEach(element => {
        price += element.price
      });
      return price.toFixed(2)
    },
    avgPrice() {
      return (this.totalPrice / this.list.length).toFixed(2)
    }
  },

  // 侦听器侦听
  watch: {
    list: {
      deep: true,
      handler(newVal, oldVal) {
        localStorage.setItem('pList', JSON.stringify(this.list))
      }
    }
  }
}

</script>

<style scoped>
.red {
  color: red;
}
.form-flex {
  display: flex;
  justify-content: start;
}
</style>
