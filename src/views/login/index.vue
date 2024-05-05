<script setup>

import {ref} from "vue"

const phoneNumber = ref()
const captcha = ref()
const smsVerificationCode = ref()

</script>

<template>
  <van-nav-bar>
    <template #left>
      <van-icon name="arrow-left" color="#181818"/>
    </template>
    <template #title>
      <div>会员登录</div>
    </template>
  </van-nav-bar>
  <van-cell-group inset>
    <template #title>
      <h1 style="color: #181818;margin-bottom: 20px;margin-top:40px ">手机登录</h1>
      <div>未注册的手机好登录后将自动注册</div>
    </template>
    <van-field v-model="phoneNumber" placeholder="请输入手机号码" required
               type="tel"/>
    <van-field v-model="captcha" placeholder="请输入图形验证码" required type="text">
      <template #right-icon>
        <van-image src="src/assets/code.png" width="20vw" height="5vh"></van-image>
      </template>
    </van-field>
    <van-field v-model="smsVerificationCode" placeholder="请输入短信验证码" required type="number">
      <template #button>
        <van-button plain color="#cea26a" size="small" type="primary">发送验证码</van-button>
      </template>
    </van-field>
  </van-cell-group>
  <van-button type="primary" size="large" style="border-radius: 10vw;background-color:#f3a72b; border-color: #f3a72b; margin-top:30px">
    登录
  </van-button>
</template>

<style scoped>
/*.van-field{
  border-bottom: #f7f5f6 1px solid;
}*/
</style>
