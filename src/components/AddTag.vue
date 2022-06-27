<template>
  <div>
    <button
      class="btn btn-primary btn-sm"
      v-if="isShowBtn"
      @click="isShowBtn = false"
    >
      +Tag
    </button>
    <input
      v-focus
      type="text"
      style="width: 70px"
      v-else
      @blur="addTag"
      @keydown.enter="addTag"
      v-model="tagName"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShowBtn: true,
      tagName: ''
    }
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus()
      }
    }
  },
  methods: {
    addTag() {
      this.isShowBtn = true
      if (this.tagName.trim() !== '') {
        this.$emit('add-tag', this.tagName)
      }
      this.tagName = ''
    }
  }
}
</script>

<style></style>
