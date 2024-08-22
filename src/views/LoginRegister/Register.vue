<template>
    <div class="box cards">
      <div class="content">
        <div class="title">注册</div>
        <div class="form">
          <el-input v-model="username" placeholder="账号" class="input-field" />
          <el-input v-model="password" type="password" placeholder="密码" class="input-field" />
          <el-input v-model="confirmPassword" type="password" placeholder="确认密码" class="input-field" />
          <el-input v-model="captcha" placeholder="图形验证码" class="input-field" />
          <el-input v-model="emailCaptcha" placeholder="邮箱验证码" class="input-field">
            <template #append>
              <el-button @click="sendEmailCaptcha">发送验证码</el-button>
            </template>
          </el-input>
          <el-button type="primary" @click="handleRegister">注册</el-button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const username = ref('');
  const password = ref('');
  const confirmPassword = ref('');
  const captcha = ref('');
  const emailCaptcha = ref('');
  
  const sendEmailCaptcha = () => {
    console.log('发送邮箱验证码至:', username.value);
    // 发送验证码的逻辑
  };
  
  const handleRegister = () => {
    console.log('账号:', username.value);
    console.log('密码:', password.value);
    console.log('确认密码:', confirmPassword.value);
    console.log('图形验证码:', captcha.value);
    console.log('邮箱验证码:', emailCaptcha.value);
    // 注册的逻辑
  };
  </script>
  
  <style lang="scss" scoped>
  .box {
    margin-left: 0.75rem;
    height: 40%;
    max-width: 50%;
    position: relative;
    border-radius: 20px;
    background-color: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(8px);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  
    .content {
      display: flex;
      flex-direction: column;
      padding: 30px;
      height: 100%;
  
      .title {
        text-align: center;
        font-size: 2rem;
        font-family: "Cursive", sans-serif;
        background: linear-gradient(90deg, #71b0c9, #0959e4);
        -webkit-background-clip: text;
        color: transparent;
        margin-bottom: 1.5rem;
      }
  
      .form {
        display: flex;
        flex-direction: column;
        gap: 1rem;
        
        .input-field {
          border-radius: 25px;
          backdrop-filter: blur(5px);
          padding: 10px 20px;
          color: #cccccc;
          
          :deep(.el-input__wrapper) {
            border: none;
            background-color: rgba(255, 255, 255, 0);
          }
        }
  
        el-button {
          border-radius: 25px;
        }
      }
    }
  }
  </style>
  