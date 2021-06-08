  <template>
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="日期" width="180">
        <template scope="scope">
          <el-date-picker v-model="scope.row.date" type="date" placeholder="选择日期"></el-date-picker>
        </template>
      </el-table-column>
      <el-table-column prop="name" label="姓名" width="180">
        <template scope="scope">
          <el-input size="small" v-model="scope.row.name" placeholder="请输入内容" @change="handleEdit(scope.$index, scope.row)"></el-input>
        </template>
      </el-table-column>
      <el-table-column prop="address" label="地址">
        <template scope="scope">
          <el-input size="small" v-model="scope.row.address" placeholder="请输入内容" @change="handleEdit(scope.$index, scope.row)"></el-input>
        </template>
      </el-table-column>
      <el-table-column prop="radio" label="单选框">
        <template scope="scope">
          <el-radio-group v-model="scope.row.radio">
            <el-radio :label="3">备选项</el-radio>
            <el-radio :label="6">备选项</el-radio>
            <el-radio :label="9">备选项</el-radio>
          </el-radio-group>
        </template>
      </el-table-column>
      <el-table-column prop="checkbox" label="复选框">
        <template scope="scope">
          <el-checkbox-group v-model="scope.row.checkbox">
            <el-checkbox label="复选框 A"></el-checkbox>
            <el-checkbox label="复选框 B"></el-checkbox>
            <el-checkbox label="复选框 C"></el-checkbox>
            <el-checkbox label="禁用"></el-checkbox>
            <el-checkbox label="选中且禁用"></el-checkbox>
          </el-checkbox-group>
        </template>
      </el-table-column>
      <el-table-column prop="checkbox" label="复选框">
        <template scope="scope">
          <el-select v-model="scope.row.select" placeholder="请选择">
            <el-option
              v-for="item in selectOptions"
              :key="item.value"
              :label="item.label"
              :value="item.value">
            </el-option>
          </el-select>
        </template>
      </el-table-column>
      <el-table-column prop="cascader" label="级联选择器">
        <template scope="scope">
          <el-cascader
            v-model="scope.row.cascader"
            :options="cascaderOptions"
            @change="handleChange">
          </el-cascader>
        </template>
      </el-table-column>
    </el-table>
  </template>

<script>

export default {
  data () {
    return {
      tableData: [],
      selectOptions: [],
      cascaderOptions: []
    }
  },
  methods: {
    handleEdit (index, row) {
      console.log(index, row)
    }
  },
  mounted () {
    // 选择器数据
    const selectOptions = []
    const cascaderOptions = []
    const tableData = []
    for (let index = 0; index < 200; index++) {
      selectOptions.push({
        value: '选项' + index,
        label: '选项' + index
      })
      cascaderOptions.push({
        value: '选项' + index,
        label: '选项' + index,
        children: [{
          value: 'cexiangdaohang',
          label: '侧向导航'
        }, {
          value: 'dingbudaohang',
          label: '顶部导航'
        }]
      })
      tableData.push({
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄',
        radio: '3',
        checkbox: '选中且禁用',
        select: '123'
      })
    }
    this.selectOptions = selectOptions
    this.cascaderOptions = selectOptions
    this.tableData = tableData
  }
}
</script>
