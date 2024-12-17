<!-- src/views/ForgetPassword.vue -->
<template>
  <div id="ForgetPassword" class="forget-password-container">
    <el-form ref="form" :model="form" label-width="80px" class="forget-password-form">
      <h2 class="form-title">找回密码</h2>
      
      <!-- 用户名 -->
      <el-form-item label="用户名" :rules="[{ required: true, message: '请输入用户名', trigger: 'blur' }]">
        <el-input placeholder="请输入用户名" v-model="form.username" clearable></el-input>
      </el-form-item>

      <!-- 邮箱 -->
      <el-form-item label="邮箱" :rules="[{ required: true, message: '请输入邮箱', trigger: 'blur' }, { type: 'email', message: '邮箱格式不正确', trigger: 'blur' }]">
        <el-input placeholder="请输入你的邮箱" v-model="form.email" clearable></el-input>
      </el-form-item>

      <!-- 验证码 -->
      <el-form-item label="验证码" :rules="[{ required: true, message: '请输入验证码', trigger: 'blur' }]">
        <el-input placeholder="请输入验证码" v-model="form.verificationCode" clearable>
          <template #append>
            <el-button type="primary" @click="sendVerificationCode">发送</el-button>
          </template>
        </el-input>
      </el-form-item>

      <!-- 新密码 -->
      <el-form-item label="新密码" :rules="[{ required: true, message: '请输入新密码', trigger: 'blur' }]">
        <el-input placeholder="请输入新密码" v-model="form.newPassword" show-password></el-input>
      </el-form-item>

      <!-- 确认密码 -->
      <el-form-item label="确认密码" :rules="[{ required: true, message: '请确认密码', trigger: 'blur' }]">
        <el-input placeholder="请再次输入密码" v-model="form.confirmPassword" show-password></el-input>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" @click="onSubmit">确定</el-button>
      </el-form-item>

      <el-form-item>
        <router-link to="/login" class="login-link">登录账号</router-link>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        username: '',
        email: '',
        verificationCode: '',
        newPassword: '',
        confirmPassword: ''
      }
    }
  },
  methods: {
    sendVerificationCode() {
      console.log('发送验证码:', this.form.email);
      // 这里可以添加发送验证码的逻辑
    },
    onSubmit() {
      console.log('提交:', this.form);
      // 这里可以添加重置密码的逻辑
    }
  }
}
</script>

<style scoped>
.forget-password-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: url('../assets/bg.png') no-repeat center center fixed;
  background-size: cover;
}

.forget-password-form {
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

.login-link {
  display: block;
  text-align: center;
  margin-top: 10px;
}
</style>