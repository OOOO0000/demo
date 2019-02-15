<template>
     <div class="index">
<el-container>
  <!-- 左边内容 -->
  <el-aside width="200px">
   <Nav></Nav>
  </el-aside>










  <el-container>



     <!-- 右边头部 -->
    <el-header>
      <Top></Top>
    </el-header>
    <!-- 右边中间 -->
    <el-main>
        <!-- 路由出口 -->
        <router-view></router-view>
    </el-main>
    <!-- 右边底部 -->
    <el-footer>
      <botton></botton>
    </el-footer>
  </el-container>
</el-container>  



     </div>


</template>
 
 <script>
 import Nav from '@/components/Nav.vue';
 import Top from '@/components/Top.vue';
 import botton from '@/components/botton/botton.vue';
export default {
  // 引入组件
       components:{
         Nav,
         Top,
         botton
       },
 
};
</script>
 
 <style lang='less'>
.index {
  height: 100%;
  .el-container {
    height: 100%;
    //   左侧
    .el-aside {
      background-color: #2d3a4b;
      color: #333;
      text-align: center;
      
    }
    //    中间
    .el-main {
      background-color: #fff;
      color: #333;
      text-align: center;
    }
    //   头部
    .el-header,
    .el-footer {
      background-color: #b3c0d1;
      color: #333;
      text-align: center;
      line-height: 60px;
    }
  }
}
</style>
 