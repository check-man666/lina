<template>
  <el-button
    :type="$attrs.type || 'primary'"
    v-bind="$attrs"
    plain
    :style="style"
    v-on="$listeners"
  >
    <slot />
  </el-button>
</template>

<script>
export default {
  data() {
    return {
      style: {
        border: 'none',
        background: 'inherit',
        padding: '9px 0'
      }
    }
  },
  mounted() {
    // 将初始color写到style里，覆盖element的hover效果
    this.style = Object.assign({}, this.style, {
      color: getComputedStyle(this.$el).color
    })
  }
}
</script>
