<template>
  <div>
    <my-table :goodsList="goodsList"></my-table>
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
