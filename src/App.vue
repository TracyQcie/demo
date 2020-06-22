<template>
  <div class="app">
    <el-menu
      background-color="#24B7C3"
      text-color="#fff"
      active-text-color="#E7F5E6"
      :default-active="activeIndex"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
    >
      <el-menu-item index="1">首页</el-menu-item>
      <el-submenu index="2">
        <template slot="title">商城</template>
        <el-menu-item index="2-1">选项1</el-menu-item>
        <el-menu-item index="2-2">选项2</el-menu-item>
        <el-menu-item index="2-3">选项3</el-menu-item>
        <el-submenu index="2-4">
          <template slot="title">选项4</template>
          <el-menu-item index="2-4-1">选项1</el-menu-item>
          <el-menu-item index="2-4-2">选项2</el-menu-item>
          <el-menu-item index="2-4-3">选项3</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="3" disabled>消息中心</el-menu-item>
      <el-menu-item index="4">
        <a href="https://www.viomi.com.cn/" target="_blank">云米官网</a>
      </el-menu-item>
    </el-menu>
    <v-content>
      <router-view></router-view>
    </v-content>
  </div>
</template>

<style>
body{
  background-color: #f2f2f2;
  padding: 0;
  margin: 0;
}
</style>

<script>
export default {
  name: "APP",
  data() {
    return {
      activeIndex: "1",
      activeIndex2: "1"
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    }
  }
};
</script>