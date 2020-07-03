<template>
  <div class="about">
    <operation-btn
      v-if="operation.describe === 'operationBten'"
      :operation="operation"
      :scope="scope"
      @handle-table-click="handleTabClick"
    ></operation-btn>
  </div>
</template>
<script>
import operationBtn from './operationBten.vue'
export default {
  components: {
    'operation-btn': operationBtn
  },
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
    handleTabClick(options, rowItem) {
      this.$emit('handle-table-click', options, rowItem);
    }
  }
}
</script>
