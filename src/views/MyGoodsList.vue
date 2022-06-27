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
        <td>
          <!-- 添加标签 -->
          <add-tag @add-tag="addTag(item.tags, $event)"></add-tag>
          <!-- 徽标 -->
          <span
            style="margin-right: 5px"
            class="badge bg-warning text-dark"
            v-for="(i, index) in item.tags"
            :key="index"
          >
            {{ i }}
          </span>
        </td>
        <td>
          <button class="btn btn-danger btn-sm" @click="delGoods(item)">
            删除
          </button>
        </td>
      </template>
    </my-table>
  </div>
</template>

<script>
import MyTable from '@/components/MyTable.vue'
import axios from '@/utils/request.js'
import AddTag from '@/components/AddTag.vue'

export default {
  components: { MyTable, AddTag },
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
    },
    delGoods(i) {
      this.goodsList = this.goodsList.filter((item) => item !== i)
    },
    addTag(tags, tagName) {
      tags.push(tagName)
    }
  }
}
</script>

<style></style>
