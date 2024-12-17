<!-- src/views/Login.vue -->
<template>
  <div id="Login" class="login-container" >
    <el-form ref="form" :model="form" label-width="80px" class="login-form">
      <h2 class="form-title">登录你的账号</h2>
      
      <!-- 用户名 -->
      <el-form-item label="用户名" :rules="[{ required: true, message: '请输入用户名', trigger: 'blur' }, { pattern: /^[\u4e00-\u9fa5_a-zA-Z0-9]+$/, message: '用户名只能包含中文字母和数字', trigger: 'blur' }]">
        <div class="input-with-tooltip">
          <el-input 
            v-model="form.username" 
            placeholder="请输入用户名" 
            @blur="checkUsername"
          ></el-input>
          <el-tooltip v-if="usernameError" class="item" effect="dark" content="用户名只能包含中文字母和数字" placement="right-start">
            <el-button icon="el-icon-warning" style="border: none; background: none;"></el-button>
          </el-tooltip>
        </div>
      </el-form-item>

      <!-- 密码 -->
      <el-form-item label="密码" :rules="[{ required: true, message: '请输入密码', trigger: 'blur' }, { min: 8, message: '密码必须大于8位', trigger: 'blur' }]">
        <div class="input-with-tooltip">
          <el-input 
            placeholder="请输入密码" 
            v-model="form.password" 
            show-password 
            @blur="checkPassword"
          ></el-input>
          <el-tooltip v-if="passwordError" class="item" effect="dark" content="密码必须大于8位" placement="right-start">
            <el-button icon="el-icon-warning" style="border: none; background: none;"></el-button>
          </el-tooltip>
        </div>
      </el-form-item>

      <!-- 添加注册和忘记密码的链接 -->
      <el-form-item>
        <div class="links">
          <router-link to="/Register">注册账号</router-link>
          <router-link to="/ForgetPassword">忘记密码</router-link>
        </div>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" class="submit-button" @click="onSubmit" link to="/Home">登录</el-button>
        <router-link to="/Home">首页</router-link>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import { Message } from 'element-ui'; // 引入 Element UI 的 Message 组件

export default {
  data() {
    return {
      form: {
        username: '', // 确保在 form 中有 username 字段
        password: ''
      },
      passwordError: false,
      usernameError: false // 添加 usernameError
    }
  },
  methods: {
    checkUsername() {
      this.usernameError = !/^[\u4e00-\u9fa5_a-zA-Z0-9]+$/.test(this.form.username);
    },
    checkPassword() {
      this.passwordError = this.form.password.length < 8;
    },
    onSubmit() {
      this.$refs.form.validate((valid) => {
        if (valid && !this.usernameError && !this.passwordError) {
          console.log('提交:', this.form);
          // 这里可以添加登录逻辑
        } else {
          Message.error('表单验证失败，请检查输入的内容'); // 弹出错误提示
        }
      });
    }
  }
}
</script>

<style scoped>


.login-container {


  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: url('../assets/bg.png') no-repeat center center fixed;
  background-size: cover;
}

.login-form {
  background: rgba(255, 255, 255, 0.8);
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  width: 400px; /* 根据需要调整宽度 */
}

.form-title {
  text-align: center;
  margin-bottom: 20px;
}

.submit-button {
  width: 100%;
}

.links {
  display: flex;
  justify-content: space-between; /* 链接之间的间距 */
  font-size: 13px; /* 字体大小 */
  align-items: center;
}

.input-with-tooltip {
  display: flex;
  align-items: center; /* 垂直居中对齐 */
}

.input-with-tooltip .el-input {
  flex: 1; /* 输入框占据剩余空间 */
  margin-right: 10px; /* 输入框和提示框之间的间距 */
}
</style>