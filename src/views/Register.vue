<template>
  <div id="Register" class="register-container">
    <el-form ref="form" :model="form" label-width="80px" class="register-form">
      <h2 class="form-title">注册你的账号</h2>

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

      <!-- 确认密码 -->
      <el-form-item label="确认密码" :rules="[{ required: true, message: '请确认密码', trigger: 'blur' }, { validator: validateConfirmPassword, trigger: 'blur' }]">
        <div class="input-with-tooltip">
          <el-input 
            placeholder="请再次输入密码" 
            v-model="form.confirmPassword" 
            show-password 
            @blur="checkConfirmPassword"
          ></el-input>
          <el-tooltip v-if="confirmPasswordError" class="item" effect="dark" content="确认密码与输入的密码不一致" placement="right-start">
            <el-button icon="el-icon-warning" style="border: none; background: none;"></el-button>
          </el-tooltip>
        </div>
      </el-form-item>

      <!-- 邮箱 -->
      <el-form-item label="邮箱" :rules="[{ required: true, message: '请输入邮箱', trigger: 'blur' }, { type: 'email', message: '邮箱格式不正确', trigger: 'blur' }]">
        <div class="input-with-tooltip">
          <el-input 
            placeholder="请输入你的邮箱" 
            v-model="form.email" 
            clearable 
            @blur="checkEmail"
          ></el-input>
          <el-tooltip v-if="emailError" class="item" effect="dark" content="请输入有效的邮箱地址" placement="right-start">
            <el-button icon="el-icon-warning" style="border: none; background: none;"></el-button>
          </el-tooltip>
        </div>
      </el-form-item>

      <!-- 验证码 -->
      <el-form-item label="验证码" :rules="[{ required: true, message: '请输入验证码', trigger: 'blur' }]">
        <div class="input-with-tooltip">
          <el-input 
            placeholder="请输入验证码" 
            v-model="form.verificationCode" 
            clearable
          >
            <template #append>
              <el-button type="primary" @click="sendVerificationCode">发送</el-button>
            </template>
          </el-input>
        </div>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" class="submit-button" @click="onSubmit">注册</el-button>
      </el-form-item>
      <el-form-item>
        <router-link to="/login" class="login-link">登录账号</router-link>
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
        password: '',
        confirmPassword: '',
        email: '',
        verificationCode: ''
      },
      passwordError: false,
      confirmPasswordError: false,
      emailError: false,
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
    checkConfirmPassword() {
      this.confirmPasswordError = this.form.confirmPassword !== this.form.password;
    },
    checkEmail() {
      this.emailError = !this.$refs.form.fields[3].validate(); // 验证邮箱格式
    },
    validateConfirmPassword(rule, value, callback) {
      if (value === this.form.password) {
        this.confirmPasswordError = false;
        callback();
      } else {
        this.confirmPasswordError = true;
        callback(new Error('确认密码与输入的密码不一致'));
      }
    },
    sendVerificationCode() {
      console.log('发送验证码:', this.form.email);
      // 这里可以添加发送验证码的逻辑
    },
    onSubmit() {
      this.$refs.form.validate((valid) => {
        if (valid && !this.usernameError && !this.passwordError && !this.emailError && !this.confirmPasswordError) {
          console.log('提交:', this.form);
          // 这里可以添加注册逻辑
        } else {
          Message.error('表单验证失败，请检查输入的内容'); // 弹出错误提示
          return false;
        }
      });
    }
  }
}
</script>

<style scoped>
.register-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: url('../assets/bg.png') no-repeat center center fixed;
  background-size: cover;
}

.register-form {
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

.login-link {
  display: block;
  text-align: center;
  margin-top: 10px;
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