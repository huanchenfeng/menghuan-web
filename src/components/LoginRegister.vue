<template>
    <!-- 登录注册 -->
    <div class="social">
      <div class="link">
        <a
          class="left-link"
          target="_blank"
          @click="handleLoginClick"
          @mouseenter="socialTip = '登录'"
          @mouseleave="socialTip = '~~~~~~~~~左边登录右边注册~~~~~~~~~'"
        >
          <img class="icon" src="/images/icon/bilibili.png" height="24" />
        </a>
        <span class="tip">{{ socialTip }}</span>
        <a
          class="right-link"
          target="_blank"
          @click="handleRegisterClick"
          @mouseenter="socialTip = '注册'"
          @mouseleave="socialTip = '~~~~~~~~~左边登录右边注册~~~~~~~~~'"
        >
          <img class="icon" src="/images/icon/bilibili.png" height="24" />
        </a>
      </div>
    </div>
  </template>
  
  <script setup>
  import { mainStore } from "@/store";
const store = mainStore();
  // 登录注册提示
  const socialTip = ref("~~~~~~~~~左边登录右边注册~~~~~~~~~");
// 切换登录注册功能区
const changeBoxOpenState = (state) => {
  if (store.getInnerWidth >= 721) {
    store.boxOpenState = state;
  } else {
    ElMessage({
      message: "当前页面宽度不足以开启盒子",
      grouping: true,
      icon: h(Error, {
        theme: "filled",
        fill: "#efefef",
      }),
    });
  }
};

// 用于区分登录和注册的点击事件
const handleLoginClick = () => {
  changeBoxOpenState(2);
};

const handleRegisterClick = () => {
  changeBoxOpenState(3);
};
  </script>
  
  <style lang="scss" scoped>
  .social {
    margin-top: 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 460px;
    width: 100%;
    height: 42px;
    background-color: transparent;
    border-radius: 6px;
    backdrop-filter: blur(0);
    animation: fade 0.5s;
    transition: background-color 0.3s, backdrop-filter 0.3s;
  
    @media (max-width: 840px) {
      max-width: 100%;
      justify-content: center;
      .link {
        justify-content: space-evenly !important;
        width: 90%;
      }
      .tip {
        display: none !important;
      }
    }
  
    .link {
      display: flex;
      align-items: center;
      justify-content: space-between; /* 使两个链接左右分布 */
      width: 100%;
  
      a {
        display: inherit;
  
        .icon {
          margin: 0 12px;
          transition: transform 0.3s;
          &:hover {
            transform: scale(1.1);
          }
          &:active {
            transform: scale(1);
          }
        }
      }
  
      .left-link {
        text-align: left; /* 左对齐 */
      }
  
      .right-link {
        text-align: right; /* 右对齐 */
      }
    }
  
    .tip {
      display: none;
      margin-right: 12px;
      animation: fade 0.5s;
    }
  
    @media (min-width: 768px) {
      &:hover {
        background-color: #00000040;
        backdrop-filter: blur(5px);
        .tip {
          display: block;
        }
      }
    }
  }
  </style>
  