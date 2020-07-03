<template>
  <div class="home">
    <ys-table
      :column="column"
      :tableData="tableData"
      @handle-table-click="handleTabClick"
      @selection-change="handleSelectionChange"
    ></ys-table>
  </div>
</template>

<script>
import Table from '../components/table.vue'
export default {
  name: 'Home',
  components: {
    'ys-table': Table
  },
  data() {
    return {
      column: [
        {
          selects: true
        },
        {
          key: '姓名',
          label: 'name'
        },
        {
          key: '年龄',
          label: 'age'
        },
        {
          key: '操作',
          sort: true,
          describe: 'operationBten',
          options: [
            {
              icon: 'el-icon-delete',
            },
            {
              icon: 'el-icon-circle-plus'
            }
          ]
        }
      ],
      tableData: [
        {
          date: '2016-05-02',
          name: '王小虎',
          age: 40
        },
        {
          date: '2016-05-02',
          name: '王二虎',
          age: 80
        }
      ]
    }
  },
  methods: {
    handleTabClick(options, rowItem) {
      console.log(options, rowItem)
    },
    handleSelectionChange(val) {
      console.log(val)
    }
  }
}
</script>
