<template>
    <div class="home">
       <el-card class="box-card">
        <div slot="header" class="clearfix">
      <span>系统管理</span>
        </div>

        <!-- 内容部分 -->
     <div  class="text item">
        <!-- 提示条 -->
         <el-alert
         title="商品总数：500,以销售总金额500，库存商品总价：500000"
         type="info"
         show-icon>
        </el-alert>

            <el-alert
         title="导入数据"
          type="success"
          show-icon>
        </el-alert>
     <!-- 内容 -->
         <el-row :gutter="20">
             <!--左边的卡片  -->
    <el-col :span="12">
        <el-card class="box-card">
    <div slot="header" class="clearfix">
     <span>商品销量</span>
    </div>
  <div  class="text item">
    <!-- 左侧表格部分 -->
        <el-table
      :data="tableData"
      style="width: 100%">
      <!-- 商品名称 -->
      <el-table-column
        prop="goodName"
        label="商品名称"
      >
      </el-table-column>
      <!-- 商品销量 -->
      <el-table-column
        prop="saleCount"
        label="商品销量"
        >
      </el-table-column>
    </el-table>
  </div>
</el-card>

    </el-col>
    <!-- 右边的卡片 -->
    <el-col :span="12">
          <el-card class="box-card">
    <div slot="header" class="clearfix">
     <span>缺货商品</span>
    </div>
  <div  class="text item">
    <!-- 右侧表格部分 -->
        <el-table
      :data="stockouData"
      style="width: 100%">
      <!-- 商品名称 -->
      <el-table-column
        prop="goodName"
        label="商品名称"
      >
      </el-table-column>
      <!-- 商品库存 -->
      <el-table-column
        prop="inventory"
        label="库存"
        >
      </el-table-column>
      <!-- 操作 -->
       <el-table-column
        prop="make"
        label="操作"
      >
       <template slot-scope="scope">
        <el-button type="text" size="small">入库</el-button>
      </template>
      </el-table-column>
    </el-table>
  </div>
</el-card>

    </el-col>
     </el-row>
         </div>
</el-card>


    </div>
</template>

<script>
export default {
  data() {
    return {
        // 商品销量
      tableData: [
       {
           goodName:"悄悄香瓜子",
           saleCount:500,
       },
        {
           goodName:"奥利奥饼干",
           saleCount:400,
       },
        {
           goodName:"旺仔小馒头",
           saleCount:500,
       },
        {
           goodName:"香飘飘奶茶",
           saleCount:550,
       },
        {
           goodName:"五香豆干",
           saleCount:500,
       },
     
      ],
    //   缺货商品
      stockouData:[
           {
               goodName:'优乐美',
               inventory:10
           },
            {
               goodName:'娃哈哈',
               inventory:20
           },
            {
               goodName:'唯一',
               inventory:10
           },
      ]
    };
  }
};
</script>

<style lang='less'>
.home {
  .el-card {
    .el-card__header {
      text-align-last: left;
      font-size: 20px;
      font-weight: 600;
      background-color: #ccc;
    }
  }
  .text {
    .el-alert {
      margin-bottom: 20px;
    }
  }
}
</style>
