<template>
  <div>
    <my-table :goodsList="goodsList">
      <template #title>
        <th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </template>
      <template #body="{ item }">
        <td>{{ item.id }}</td>
        <td>{{ item.goods_name }}</td>
        <td>{{ item.goods_price }}</td>
        <td>{{ item.tags }}</td>
        <td><button class="btn btn-danger btn-sm">删除</button></td>
      </template>
    </my-table>
  </div>
</template>

<script>
import MyTable from '@/components/MyTable.vue'
import axios from '@/utils/request.js'

export default {
  components: { MyTable },
  data() {
    return {
      goodsList: []
    }
  },
  created() {
    this.getGoods()
  },
  methods: {
    async getGoods() {
      const { data } = await axios({ url: '/api/goods' })
      this.goodsList = data.data
    }
  }
}
</script>

<style></style>
