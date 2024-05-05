<script setup>
import {ref} from 'vue'

const active = ref(0);
</script>

<template>
  <div class="category">
    <van-nav-bar #title>
      <div>全部分类</div>
    </van-nav-bar>
    <van-search v-model="value" placeholder="请输入搜索关键词" background="#f1f1f2" shape="round"/>
    <main>
      <div class="left">
        <van-sidebar v-model="active">
          <van-sidebar-item title="标签名称" v-for="(item,index) in 15" :key="index"/>
        </van-sidebar>
      </div>
      <div class="right">
        <van-row :gutter="[30,20]" v-for="(item,index) in 5" :key="index" style="margin: 15px 10px">
          <van-col span="8" v-for="(item,index) in 3">
            <van-image src="src/assets/categood.png"></van-image>
            <p style="text-align: center">手机</p>
          </van-col>
        </van-row>
      </div>

    </main>
  </div>

</template>

<style scoped>
.category{
  height: 100vh;
}
main{
  display: flex;
  height: 100%;
  .van-sidebar {
    overflow-y:auto;
    height: 100%;
  }
}

</style>
