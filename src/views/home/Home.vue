<template>
  <div>
    <NavBar class="home-nav"><div slot="center">购物街</div></NavBar>
  </div>
</template>

<script>
  import NavBar from "components/common/navbar/NavBar";
  import {getHomeMultidata} from "network/home";

  export default {
    name: "Home",
    components: {
      NavBar
    },
    data() {
      return {
        banners: [],
        recommends: []
      }
    },
    created() {
      return getHomeMultidata().then(res=>{
        console.log(res)
        this.banners = res.data.banner.list
        this.recommends = res.data.recommend.list
      })
    }
  }
</script>

<style scoped>
.home-nav{
  background: var(--color-tint);
  color: #f6f6f6;
}
</style>
