<template>
  <div class="home">
    <el-table
      :data="tableData"
      style="width: 100%">
      <template v-for="(item, index) in column">
        <el-table-column
          v-if="!item.sort && !item.selects"
          :key="index"
          :label="item.key"
          :prop="item.label">
        </el-table-column>
        <el-table-column
          v-if="item.selects"
          :key="item.label"
          type="selection"
          width="55"
          @selection-change="handleSelectionChange"
        >
        </el-table-column>
        <el-table-column
          v-if="item.sort"
          :key="item.lable"
          :label="item.key"
          :prop="item.label"
         >
          <template slot-scope="scope">
            <operation-all :scope="scope.row" :operation="item" @handle-table-click="handleTabClick"></operation-all>
          </template>
        </el-table-column>
      </template>
    </el-table>
  </div>
</template>

<script>
import operationAll from './operationAll/index';
export default {
  props: {
    // 表头 必传
    column: {
      type: Array, 
      require: true
    },
    // 数据 必传
    tableData: {
      type: Array,
      require: true
    }
  },
  components: {
    'operation-all': operationAll
  },
  data() {
    return {
    }
  },
  methods: {
    handleTabClick(options, rowItem) {
      this.$emit('handle-table-click', options, rowItem);
    },
    handleSelectionChange(val) {
      console.log(val)
      this.$emit('selection-change', val);
    }
  },
}
</script>
