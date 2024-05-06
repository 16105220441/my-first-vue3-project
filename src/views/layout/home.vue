<script setup>
import {ref,onBeforeMount} from "vue"
import GoodsItem from "@/components/GoodsItem.vue";
import {getHomeData} from "@/api/home.js";
const list = ref([]);
const loading = ref(false);
const finished = ref(false);
let bannerList = []
let navList = []
let proList = []

const getPageDate = async ()=>{
  let {data:{
    pageData:{
      items
    }
  }} = await getHomeData()
  // console.log('items',items)
  if(items){
    bannerList = items[1].data
    navList = items[3].data
    proList = items[6].data
  }
}
getPageDate()
const onLoad = () => {
  // 异步更新数据
  // setTimeout 仅做示例，真实场景中一般为 ajax 请求
  setTimeout(() => {
    for (let i = 0; i < 10; i++) {
      list.value.push(list.value.length + 1);
    }

    // 加载状态结束
    loading.value = false;

    // 数据全部加载完成
    if (list.value.length >= 40) {
      finished.value = true;
    }
  }, 1000);
};
</script>

<template>
  <van-nav-bar title="智慧商城" fixed></van-nav-bar>
  <van-search v-model="value" placeholder="请输入搜索关键词" background="#f1f1f2" readonly shape="round"/>
  <main>
    <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">

      <van-swipe-item v-for="(item,index) in bannerList" :key="index">
        <img :src="item.imgUrl" alt="">
      </van-swipe-item>
<!--      <van-swipe-item>
        <img src="@/assets/banner2.jpg" alt="">
      </van-swipe-item>
      <van-swipe-item>
        <img src="@/assets/banner3.jpg" alt="">
      </van-swipe-item>-->
    </van-swipe>

    <van-grid :column-num="5">
      <van-grid-item v-for="value in 10" :key="value" icon="photo-o" text="文字"/>
    </van-grid>

    <div class="main">
      <img src="@/assets/main.png" alt="">
    </div>
    <div class="guess">
      <p class="guess-title">——猜你喜欢——</p>
      <van-list
          v-model:loading="loading"
          :finished="finished"
          finished-text="没有更多了"
          @load="onLoad"
      >
        <van-cell v-for="item in list" :key="item">
          <GoodsItem></GoodsItem>
        </van-cell>
      </van-list>
    </div>

  </main>

</template>

<style lang="less" scoped>

.van-nav-bar {
  z-index: 999;
  background-color: #c21401;

  ::v-deep .van-nav-bar__title {
    color: #ffffff;
  }
}

.van-search {
  position: fixed;
  left: 0;
  right: 0;
  width: 100%;
  top: 46px;
  z-index: 999;
  padding-left: 0;
  padding-right: 0;
}

main {
  position: relative;
  top: 100px
}

.my-swipe {
  .van-swipe-item {
    height: 185px;
    color: #fff;
    font-size: 20px;
    text-align: center;
    background-color: #39a9ed;

    img {
      width: 100%;
      height: 185px;
    }
  }
}
.main img {
  display: block;
  width: 100%;
}
.guess {
  .guess-title{
    height:40px;
    line-height: 40px;
    text-align: center;
  }
  .van-list{
    background-color: #f6f6f6;
  }

}

</style>
