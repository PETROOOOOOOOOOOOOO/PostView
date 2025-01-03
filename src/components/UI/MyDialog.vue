<template>
  <div class="dialog" v-if="show" @click.stop="hideDialog">
    <div @click.stop class="dialog-header">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'myDialog',
  props: {
    show: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hideDialog() {
      this.$emit('update:show', false);
    }
  }
}
</script>

<style scoped>
.dialog {
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background: rgba(0, 0, 0, .5);
  position: fixed;
  display: flex;
}

.dialog-header {
  margin: auto;
  background: azure;
  border-radius: 15px;
  min-height: 50px;
  min-width: 300px;
  padding: 30px;
}
</style>