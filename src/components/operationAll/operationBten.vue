<template>
  <div class="about">
    <i v-for="(item, indexs) in operation.options" :key="indexs" :class="item.icon" @click="handleTabClick(item)"></i>
  </div>
</template>
<script>
export default {
  props: {
    // 表头 必传
    scope: {
      type: Object, 
      require: true
    },
    // 数据 必传
    operation: {
      type: Object,
      require: true
    }
  },
  methods: {
    handleTabClick(options) {
      this.$emit('handle-table-click', options, this.scope);
    }
  },
}
</script>
