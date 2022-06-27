<template>
  <div class="my-tab-bar">
    <div
      :class="['tab-item', { current: currentIndex === index }]"
      v-for="(item, index) in tabList"
      :key="index"
      @click="changeComponent(item.componentName,index)"
    >
      <!-- 图标 -->
      <span :class="`iconfont ${item.iconText}`"></span>
      <!-- 文字 -->
      <span class="text">{{ item.text }}</span>
    </div>
  </div>
</template>

<script>
// validator 校验器 函数形式
export default {
  props: {
    tabList: {
      type: Array,
      required: true,
      validator(data) {
        const len = data.length
        return len > 2 && len < 5
        /* if (len > 2 && len < 5) {
          return true
        } else {
          return false
          // throw new Error('tablist数组长度必须在2-5之间')
        } */
      }
    }
  },
  data() {
    return {
      currentIndex: 0
    }
  },
  methods: {
    changeComponent(componentName, index) {
      this.currentIndex = index
      this.$emit('change-component', componentName)
    }
  }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;

  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    cursor: pointer;
  }
}

.text {
  margin-bottom: 8px;
}

.current {
  color: #1d7bff;

  .iconfont {
    color: #1d7bff;
  }
}
</style>
