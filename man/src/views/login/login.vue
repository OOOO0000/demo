<template>
    <div class="login">
     <div class="login-wrop">
         <!-- 表单标题 -->
         <div class="title">
         <i class="el-icon-menu">
         欢迎来到华联超市系统-登录
         </i>
         </div>
         <!-- 登录表单 -->
     <el-form :model="loginFrom" status-icon :rules="rules" ref="loginFrom" label-width="100px" class="demo-ruleForm">

        <el-form-item label="账号" prop="uesrname">
        <el-input type="text" v-model="loginFrom.uesrname" autocomplete="off"></el-input>
        </el-form-item>
            
         <el-form-item label="密码" prop="password">
        <el-input type="password" v-model="loginFrom.password" autocomplete="off"></el-input>
        </el-form-item>

        <el-form-item label="确认密码" prop="checkPwd">
            <el-input type="password" v-model="loginFrom.checkPwd" autocomplete="off"></el-input>
        </el-form-item>


        <el-form-item>
            <el-button type="primary" @click="submitForm('loginFrom')">登录</el-button>
            <el-button @click="resetForm('loginFrom')">重置</el-button>
        </el-form-item>

    </el-form>

         
     </div>
    </div>

</template>


<script>
export default {
  data() {
    //密码认真的函数
    const pass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("请输入密码"));
      } else if (value.length < 3 || value.length > 6) {
        callback(new Error("请输入真正确格式"));
      } else if (this.loginFrom.checkPwd !== "") {
        this.$refs.loginFrom.validateField("checkPwd");
      }
      callback();
    };

    //确认密码的验证
    const checkPass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error("请在此输入密码"));
      } else if (value !== this.loginFrom.password) {
        callback(new Error("两次输入密码不一致"));
      }
      callback();
    };
    return {
      loginFrom: {
        uesrname: "",
        password: "",
        checkPwd: ""
      },
      //这是验证失去焦点
      rules: {
        //用户名
        uesrname: [
          { required: true, message: "请输入用户名", trigger: "blur" },
          { min: 3, max: 5, message: "长度在 3 到 5 个字符", trigger: "blur" }
        ],
        //密码
        password: [{ required: true, validator: pass, trigger: "blur" }],
        //确认密码
        checkPwd: [{ required: true, validator: checkPass, trigger: "blur" }]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("恭喜你登录成功");

          let params = {
            uesrname: this.loginFrom.uesrname,
            password: this.loginFrom.password
          };
          //    直接跳转后端也面
          // console.log(params)
          this.$router.push("/");
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

<style lang="less">
.login {
  height: 100%;
  height: 100%;
  background-color: #2d3a4b;

  .login-wrop {
    width: 500px;
    height: 300px;
    border-radius: 8px;
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;
    background-color: rgba(0, 0, 0, 0.2);
    color: #ffffff;
    padding: 30px 60px 10px 10px;
    .title {
      font-size: 20px;
      margin-left: 55px;
      margin-bottom: 20px;
    }
    .el-form {
      .el-form-item {
        .el-form-item__label {
          color: #ffffff;
        }
      }
    }
  }
}
</style>
