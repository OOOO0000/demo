<template>
    
    <div class="accountadd">
        <!-- 面板组件 -->
        <el-card class="box-card">
        <div slot="header" class="clearfix">
      <span>添加账号</span>
        </div>

        <!-- 内容部分 -->
     <div  class="text item">
         <!-- 添加账号表单 -->
      <el-form :model="addFrom" status-icon :rules="rules" ref="addFrom" label-width="100px" class="demo-ruleForm">

        <el-form-item label="账号" prop="uesrname">
        <el-input type="text" v-model="addFrom.uesrname" autocomplete="off"></el-input>
        </el-form-item>
            
         <el-form-item label="密码" prop="password">
        <el-input type="password" v-model="addFrom.password" autocomplete="off"></el-input>
        </el-form-item>

        <el-form-item label="确认密码" prop="checkPwd">
            <el-input type="password" v-model="addFrom.checkPwd" autocomplete="off"></el-input>
        </el-form-item>
          <!-- 选着用户组 -->
          <el-form-item label="选择用户组" prop="uesegroup">
         <el-select v-model="addFrom.uesegroup" placeholder="用户组">
         <el-option label="vip管理" value="vip管理"></el-option>
         <el-option label="普通用户" value="普通用户"></el-option>
        </el-select>
         </el-form-item>
     

        <el-form-item>
            <el-button type="primary" @click="submitForm('addFrom')">添加</el-button>
            <el-button @click="resetForm('addFrom')">重置</el-button>
        </el-form-item>

    </el-form>
     </div>
</el-card>

    </div>
</template>

<script>
export default {
  data() {
    //   验证密码的函数
    const pass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("密码不能为空"));
      } else if (value.length < 3 || value.length > 6) {
        callback(new Error("请输入正确密码格式"));
      } else{
        if(this.addFrom.checkPwd!==""){
           this.$refs.addFrom.validateField("checkPwd");
        }
      }
        callback();
    };
    //   验证确实密码
    const checkpwd = (rule, value, callback) => {
      if(value=== ""){
         callback(new Error("密码不能为空"));
      } else if(value !==this.addFrom.password) {
        callback(new Error("两次密码不一至"));
      }
        callback();
      
    };
    return {
      addFrom: {
        uesrname: "",
        password: "",
        checkPwd: "",
        uesegroup: ""
      },
      // 验证规则
      rules: {
        //  账号
        uesrname: [
          { required: true, message: "请输入账号", trigger: "blur" },
          { min: 3, max: 6, message: "长度在3-6位" }
        ],
        // 密码
        password: [
          { required: true, validator: pass, trigger: "blur" }
        ],
        // 确认密码
        checkPwd: [
          { required: true, validator: checkpwd, trigger: "blur" }
        ],
        // 用户组
         uesegroup:[
           { required: true, message: '请选择用户', trigger: 'change' }
         ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("恭喜你登录成功");

          let params = {
            uesrname: this.addFrom.uesrname,
            password: this.addFrom.password,
            uesegroup:this.addFrom.uesegroup
          };
          console.log(params)
          
          //跳转到管理页面
          this.$router.push("/accountmanage")

          
          // this.$router.push("/");
        } else {
          alert("登录失败");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>


<style lang='less'>
.accountadd {
  .el-card {
    .el-card__header {
      text-align-last: left;
      font-size: 20px;
      font-weight: 600;
      background-color: #ccc;
    }
    .el-card__body {
      .el-form {
        width: 400px;
        .el-form-item {
          height: 30px;
          line-height: 30px;
          .el-form-item__content {
            height: 30px;
            line-height: 30px;
            .el-input {
              height: 30px;
              line-height: 30px;
              .el-input__inner {
                height: 30px;
                line-height: 30px;
              }
            }
          }
        }
      }
    }
  }
}
</style>
