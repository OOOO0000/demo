<template>
    
    <div class="accountmanage">
        <el-card class="box-card">
        <div slot="header" class="clearfix">
      <span>添加账号</span>
        </div>

        <!-- 内容部分 -->
     <div  class="text item">
       <!-- 表格 -->
            <el-table
            ref="multipleTable"
            :data="tableData"
            tooltip-effect="dark"
            style="width: 100%"
            @selection-change="handleSelectionChange">
             <!-- 单选框 -->
            <el-table-column
            type="selection"
            width="55">
            </el-table-column>
                <!-- 账号 -->
            <el-table-column
            prop="username"
            label="账号"
            >
            </el-table-column>

             <el-table-column
            prop="usergroup"
            label="用户组"
            >
            </el-table-column>

             <!-- 日期 -->
            <el-table-column
            label="日期"
            >
            <template slot-scope="scope">{{ scope.row.ctime }}</template>
            </el-table-column>
                <!-- 操作 -->
          <el-table-column label="操作">
                <template slot-scope="scope">
                    <el-button
                    size="mini"
                    @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
                    <el-button
                    size="mini"
                    type="danger"
                    @click="handleDelete(scope.$index, scope.row)">删除</el-button>
                </template>
          </el-table-column>
           
        </el-table>
     </div>
</el-card>
    </div>
</template>

<script>
export default {
  data() {
    return {
        tableData:[
            {
                username:"",
                usergroup:'',
                ctime:'',
            }
        ]
    };
  },
  methods: {
    handleSelectionChange(val) {
      this.multipleSelection = val;
    },
    handleEdit(){

    },
    handleDelete(){

    }
  }
};
</script>

<style lang='less'>
.accountmanage {
  .el-card {
    .el-card__header {
      text-align-last: left;
      font-size: 20px;
      font-weight: 600;
      background-color: #ccc;
    }
  }
}
</style>
