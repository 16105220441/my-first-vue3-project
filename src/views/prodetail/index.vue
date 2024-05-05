<script setup>
import {ref} from 'vue';

const active = ref(0);
const onChange = (index) => showToast(`标签 ${index}`);

</script>

<template>
  <router-view></router-view>
  <van-tabbar v-model="active" @change="onChange" active-color="#ee0a24">
    <van-tabbar-item icon="wap-home-o">首页
    </van-tabbar-item>
    <van-tabbar-item icon="apps-o">分类</van-tabbar-item>
    <van-tabbar-item icon="shopping-cart-o">购物车</van-tabbar-item>
    <van-tabbar-item icon="user-o">我的</van-tabbar-item>
  </van-tabbar>
</template>

<style scoped>

</style>
