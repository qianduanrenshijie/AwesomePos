<template>
  <div class="home">
      <left-nav></left-nav>
      <div class="main">
        <router-view></router-view>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import leftNav from "@/components/common/LeftNav.vue";

export default {
  name: "home",
  components: {
    leftNav
  }
};
</script>
<style lang="scss">
.home{
  width: 100%;
  height: 100%;
  background-color: #e9eef3;
  .main{
    width: 100%;
    height: 100%;
    padding-left: 60px;
    box-sizing: border-box;
  }
}
</style>

