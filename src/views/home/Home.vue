<template>
  <div id="home" >
      <NavBar class="home-nav">
        <div slot="center">首页</div>
      </NavBar>
      <HomeSwiper :banners="banners"></HomeSwiper>
      <RecommendView :recommend="recommend"></RecommendView>
  </div>
</template>

<script>
  import NavBar from "components/common/navbar/NavBar"
  import HomeSwiper from "./childComps/HomeSwiper"
  import RecommendView from "./childComps/RecommendView"

  import {getHomeMultidata} from "network/home"
  export default {
    name: "Home",
    components: {
      NavBar,
      HomeSwiper,
      RecommendView
    },
    data() {
      return {
        banners:[],
        recommend:[],
      }
    },
    created() {
      getHomeMultidata().then( res => {
        this.banners = res.data.banner.list
        this.recommend = res.data.recommend.list
      })
    }
  }
</script>

<style scoped>
  .home-nav {
    background-color: var(--color-tint);
    color: #fff;
  }
</style>
