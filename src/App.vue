<template>
  <div id="app">
    <el-container class="app-out-panel">
      <el-header class="sys-header">一张图项目系统</el-header>
      <el-container class="app-content-panel">

        <el-aside class="sys-menu">
          <el-menu default-active="1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose"
            background-color="#545c64" text-color="#fff" active-text-color="#ffd04b" :collapse="true">

            <el-menu-item index="1">
              <i class="el-icon-monitor"></i>
              <span slot="title">首页大屏</span>
            </el-menu-item>

            <el-menu-item index="2">
              <i class="el-icon-picture-outline"></i>
              <span slot="title">一张图</span>
            </el-menu-item>
          </el-menu>
        </el-aside>

        <el-main class="sys-content">
          <Mapview />
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import Mapview from './components/common/Mapview';
export default {
  name: 'App',
  components: {
    Mapview,
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    }
  }
}
</script>

<style>
html,
body,
#app {
  position: relative;
  width: 100%;
  height: 100%;
  margin: 0;
}

.app-out-panel,
.app-content-panel {
  height: 100%;
}

.sys-header {
  background-color: #32373e;
  line-height: 60px;
  color: #fff;
  font-size: 20px;
  font-weight: 600;
}

.sys-menu {
  width: 64px !important;
  background: #545c64;
}

.sys-content {
  padding: 5px !important;
}

/* .el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 200px;
  min-height: 400px;
} */
</style>
