<template>
  <div id="app">
    <el-container class="app-out-panel">
       <el-header class="sys-header">一张图项目系统</el-header>
       <el-container class="app-content-panel">
          <el-aside width="200px" class="sys-menu">左侧菜单</el-aside>
          <el-main>地图区域</el-main>
       </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: { }
}
</script>

<style>
html,body,#app {
  position: relative;
  width: 100%;
  height: 100%;
  margin: 0;
}
.app-out-panel,.app-content-panel{
  height: 100%;
}
.sys-header{
  background:#409EFF;
  line-height: 60px;
  color: #fff;
  font-size: 20px;
}
.sys-menu{
  background:#C0C4CC;
}

</style>
