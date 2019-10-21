<template>
  <div class="login">
    <header class="login-header">
      <img :src="imgurl" alt="logo" />
      <h1>vue项目: 后台管理系统</h1>
    </header>
    <section class="login-content">
      <h2>用户登陆</h2>
      <el-form :model="userForm" status-icon :rules="rules" ref="userForm" class="login-form">
        <el-form-item prop="userName">
          <el-input
            prefix-icon="el-icon-user"
            placeholder="用户名"
            style="color: rgba(0,0,0,.25)"
            v-model="userForm.userName"
            autocomplete="off"
          ></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input
            prefix-icon="el-icon-goods"
            placeholder="密码"
            style="color: rgba(0,0,0,.25)"
            v-model="userForm.password"
            autocomplete="off"
            type="password"
          ></el-input>
        </el-form-item>
        <el-form-item>
          <el-button class="login-form-button" type="primary" @click="submitForm('userForm')">登录</el-button>
        </el-form-item>
      </el-form>
    </section>
  </div>
</template>

<script>
import logo from "../assets/logo.png";

export default {
  name: "login",
  data() {
    return {
      imgurl: logo,
      userForm: {
        username: "",
        password: ""
      },
      rules: {
        userName: [
          { required: true, message: "用户名必须输入", trigger: "blur" },
          { min: 4, max: 12, message: "长度在4到12个字符", trigger: "blur" }
        ],
        password: [{ required: true, message: "密码必须输入", trigger: "blur" }]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.login {
  width: 100%;
  height: 100%;
  position: fixed;
  background-image: url("../assets/login/bg.jpg");
  background-size: 100% 100%;
  .login-header {
    display: flex;
    align-items: center;
    height: 80px;
    background-color: rgba(21, 20, 13, 0.5);
    img {
      width: 40px;
      height: 40px;
      margin: 0 15px 0 50px;
    }
    h1 {
      font-size: 30px;
      color: white;
    }
  }

  .login-content {
    width: 400px;
    height: 300px;
    background-color: #fff;
    margin: 50px auto;
    padding: 20px 40px;
    h2 {
      text-align: center;
      font-size: 30px;
      font-weight: bold;
      margin-bottom: 20px;
    }
    .login-form {
      .login-form-button {
        width: 100%;
      }
    }
  }
}
</style>
