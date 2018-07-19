
<template>
  <div>
    <span>选中了{{multipleSelection}}个框</span>
    <br>
    <el-date-picker
      v-model='month'
      type='date'
      placeholder='选择月'
    >
    </el-date-picker>
    <el-input type='text' size='medium'  placeholder='请输入姓名进行筛选' style='width:220px' v-model='search'></el-input>
    <el-table :data='tableData' border ref='table'  style='width: 100%' @selection-change='handleSelectionChange'>
      <el-table-column type='selection' width='55'>
      </el-table-column>

      <el-table-column align='center' label='日期' width='120'>
        <template slot-scope='scope'>{{ scope.row.date }}</template>
      </el-table-column>

      <el-table-column align='center' prop='name' label='姓名' width='120'>
      </el-table-column>

      <el-table-column align='center' prop='address' label='地址' show-overflow-tooltip>
        <template slot-scope='scope'>
          <span v-show='!scope.row.editing'>{{scope.row.address}}</span>
          <el-input type='text' v-show='scope.row.editing' v-model='scope.row.address' placeholder='请输入内容' suffix-icon='el-icon-edit'></el-input>
        </template>
      </el-table-column>

      <el-table-column
        align='center'
        fixed='right'
        label='操作'
        width='450'>
        <template slot-scope='scope'>
          <el-button @click='editHandler(scope.row)' type='info' size='mini' v-show='!scope.row.editing' icon='el-icon-edit'>编辑</el-button>
          <el-button @click='saveHandler(scope.row, scope.column, scope.$index)' type='warning' size='mini' v-show='scope.row.editing' icon='el-icon-document' style='margin-left:0'>保存</el-button>
          <el-button @click='removeHandler(scope.row,scope.$index)' type='danger' size='mini' icon='el-icon-delete'>删除</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        tableData: [
          {
            date: '2018-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-05',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-05',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-06',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-07',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-08',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-09',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          },
          {
            date: '2018-10',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
            editing: false
          }
        ],
        multipleSelection: 0,
        month: '',
        search: ''
      }
    },
    mounted () {
      this.checked()
    },
    watch: {
      search (val) {
        this.tableData.search = val
      },
      month (val) {}
    },
    methods: {
      checked () {
        for (let i = 0; i < 20; i++) {
          this.$refs.table.toggleRowSelection(this.tableData[i], true)
        }
      },
      handleSelectionChange (val) {
        this.multipleSelection = val.length
      },
      detailHandler () {},
      editHandler (row) {
        row.editing = true
      },
      saveHandler (row) {
        row.editing = false
      },
      removeHandler () {
        this.tableData.splice(index, 1)
      }
    }
  }
</script>

<style>

</style>
