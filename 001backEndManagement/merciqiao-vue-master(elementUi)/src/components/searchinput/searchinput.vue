<template >
    <!-- 查询区----start -->
    <div class="container">
        <el-form :label-position="labelPosition" :label-width="labelWidth" :inline="true" :model="formInline" class="demo-form-inline">
            <el-form-item label="电器名称">
                <el-select v-model="formInline.name" placeholder="电器名称">
                    <el-option label="冰箱" value="冰箱"></el-option>
                    <el-option label="彩电" value="彩电"></el-option>
                    <el-option label="空调" value="空调"></el-option>
                    <el-option label="洗衣机" value="洗衣机"></el-option>
                </el-select>
            </el-form-item>
           <el-form-item label="开始时间">
             <input type="date" v-model="formInline.startDate"  placeholder="" style="width:200px;height:35px; border-radius: 5px;outline:none;border:1px solid #999">
           </el-form-item>
          <el-form-item label="结束时间">
            <input type="date" v-model="formInline.endDate" placeholder="" style="width:200px;height:35px; border-radius: 5px;outline:none;border:1px solid #999">
          </el-form-item>
          <!--<el-form-item label="结束日期">-->
            <!--<el-date-picker type="date" placeholder="选择日期" v-model="formInline.endDate" style="width: 100%;"></el-date-picker>-->
          <!--</el-form-item>-->
          <!--<el-form-item label="审批人">-->
                <!--<el-input v-model="formInline.user" placeholder="审批人"></el-input>-->
            <!--</el-form-item>-->
            <!--<el-form-item label="审批人">-->
                <!--<el-input v-model="formInline.user" placeholder="审批人"></el-input>-->
            <!--</el-form-item>-->
            <!--<el-form-item label="审批人">-->
                <!--<el-input v-model="formInline.user" placeholder="审批人"></el-input>-->
            <!--</el-form-item>-->
            <!--<el-form-item label="审批人">-->
                <!--<el-input v-model="formInline.user" placeholder="审批人"></el-input>-->
            <!--</el-form-item>-->
            <!--<el-form-item label="审批人">-->
                <!--<el-input v-model="formInline.user" placeholder="审批人"></el-input>-->
            <!--</el-form-item>-->
            <el-form-item label=" " >
                <el-button type="primary" @click="onSubmit">查询</el-button>
            </el-form-item>
        </el-form>
      <!--展示查询情况的表格-->
      <el-table :data="tableData" border stripe style="width: 100%" @selection-change="handleSelectionChange">
        <el-table-column type="selection" width="55">
        </el-table-column>

        <el-table-column prop="name" label="名称" width="180" sortable>
        </el-table-column>
        <el-table-column prop="brand" label="品牌" width="180" sortable>
        </el-table-column>
        <el-table-column prop="model" label="型号" sortable>
        </el-table-column>
        <el-table-column prop="quantity" label="数量" 数量>
        </el-table-column>
        <el-table-column label="操作" fixed="right" min-width="180">
          <template slot-scope="scope">
            <el-button size="mini" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
            <el-button size="mini" type="danger" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
    <!-- 查询区----end -->
</template>
<style lang="scss">
// 设置输入框的宽度
.el-form-item__content {
     width: 220px;
}
</style>
<script>
export default {
    name: 'searchinput',
    data() {
        return {
            formInline: {   //表单对象
                name: '',
                startDate: '',
                endDate: ''
            },
            labelPosition: 'right', //lable对齐方式
            labelWidth: '80px' ,  //lable宽度
          tableData:[
            {
              name:'冰箱',
              brand:'海信',
              model:'v-12',
              quantity:12
            },
            {
              name:'冰箱',
              brand:'海信',
              model:'v-12',
              quantity:12
            },
            {
              name:'冰箱',
              brand:'海信',
              model:'v-12',
              quantity:12
            },
            {
              name:'冰箱',
              brand:'海信',
              model:'v-12',
              quantity:12
            },
            {
              name:'冰箱',
              brand:'海信',
              model:'v-12',
              quantity:12
            },
          ],
          multipleSelection: []
        }
    },
    methods: {
        onSubmit() {
          var vm=this;
            console.log(vm.formInline);
        },
      handleEdit(index,row){
          console.log(index);
          console.log(row);
      },
      handleSelectionChange(val) {
        var vm=this;
        vm.multipleSelection = val;
        console.log(vm.multipleSelection);
        this.$message({
          message: '选中的项是:' + JSON.stringify(vm.multipleSelection),
          type: "success"
        });
      },
    }
}
</script>
