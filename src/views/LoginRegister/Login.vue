<template>
    <div class="box cards" @mouseenter="closeShow = true" @mouseleave="closeShow = false">
      <transition name="el-fade-in-linear">
        <close-one
          class="close"
          theme="filled"
          size="28"
          fill="#ffffff60"
          v-show="closeShow"
          @click="store.boxOpenState = 0"
        />
      </transition>
      <transition name="el-fade-in-linear">
        <setting-two
          class="setting"
          theme="filled"
          size="28"
          fill="#ffffff60"
          v-show="closeShow"
          @click="store.setOpenState = true"
        />
      </transition>
      <div class="content">
        <div class="title">登录</div>
        <div class="form">
          <el-input v-model="username" placeholder="账号" class="input-field" />
          <el-input v-model="password" type="password" placeholder="密码" class="input-field" />
          <el-button type="primary" @click="handleLogin">登录</el-button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { CloseOne, SettingTwo } from "@icon-park/vue-next";
  import { mainStore } from "@/store";
  
  const store = mainStore();
  const closeShow = ref(false);
  
  const username = ref('');
  const password = ref('');
  
  const handleLogin = () => {
    console.log('账号:', username.value);
    console.log('密码:', password.value);
  };
  </script>
  
  <style lang="scss" scoped>
  .box {
    flex: 1 0 0%;
    margin-left: 0.75rem;
    height: 40%;
    max-width: 50%;
    position: relative;
    animation: fade 0.5s;
    border-radius: 20px;
    background-color: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(8px);
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  
    &:hover {
      transform: scale(1);
    }
  
    .close,
    .setting {
      position: absolute;
      top: 14px;
      right: 14px;
      width: 28px;
      height: 28px;
      transition: transform 0.3s, opacity 0.3s;
  
      &:hover {
        transform: scale(1.2);
      }
  
      &:active {
        transform: scale(1);
      }
    }
  
    .setting {
      right: 56px;
    }
  
    .content {
      display: flex;
      flex-direction: column;
      padding: 30px;
      width: 100%;
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
            box-shadow: 0 0 0 0px var(--el-input-border-color, var(--el-border-color)) inset;
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