<template>
  <div v-show="visible" class="dialog-box">
    弹层组件
    <span @click="close">关闭</span>
    <div>
      <slot name="footer" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyDialog',
  data() {
    return {}
  },

  props: {
    visible: {
      type: Boolean,
      required: true,
    },
    beforeClose: {
      type: Function,
    },
  },

  watch: {
    visible(val) {
      if (!val) return this.$emit('close')
      this.$emit('open')
    },
  },

  created() {},

  methods: {
    close() {
      this.beforeClose()
      this.$emit('update:visible', false)
    },
  },
}
</script>

<style scoped lang="scss">
.dialog-box {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: #ccc;
  top: 0;
  left: 0;
  z-index: 9999999999999999999999;
}
</style>
