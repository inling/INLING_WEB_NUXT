<template>
  <el-container>
    <el-header>
      <el-menu :default-active="activeIndex" 
                active-text-color="#ffd04b" 
                class="el-menu-demo" 
                mode="horizontal">
        <el-menu-item index="1">英灵</el-menu-item>
        <el-menu-item index="2">编程技术</el-menu-item>
        <el-menu-item index="3">Study Timeline</el-menu-item>
        <el-menu-item index="4">do you like music？</el-menu-item>
      </el-menu>
    </el-header>
    <el-container>
      <el-aside>
        <el-menu class="el-menu-vertical-demo" 
                :collapse="true" 
                active-text-color="#ffd04b">
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span slot="title">导航一</span>
            </template>
            <el-menu-item-group>
              <span slot="title">分组一</span>
              <el-menu-item index="1-1">选项1</el-menu-item>
              <el-menu-item index="1-2">选项2</el-menu-item>
            </el-menu-item-group>
            <el-menu-item-group title="分组2">
              <el-menu-item index="1-3">选项3</el-menu-item>
            </el-menu-item-group>
            <el-submenu index="1-4">
              <span slot="title">选项4</span>
              <el-menu-item index="1-4-1">选项1</el-menu-item>
            </el-submenu>
          </el-submenu>
          <el-menu-item index="2">
            <i class="el-icon-menu"></i>
            <span slot="title">导航二</span>
          </el-menu-item>
          <el-menu-item index="3" disabled>
            <i class="el-icon-document"></i>
            <span slot="title">导航三</span>
          </el-menu-item>
          <el-menu-item index="4">
            <i class="el-icon-setting"></i>
            <span slot="title">导航四</span>
          </el-menu-item>
        </el-menu>
      </el-aside>
      <el-main>
        bvjb
        <nuxt />
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
  export default {
    data() {
      return {
        activeIndex: '1',
        activeIndex2: '1',
        isCollapse: true
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }, 
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>

<style lang="scss">
  .el-container{
    .el-header{
      .el-menu--horizontal {
        &>.el-menu-item.is-active{
          border-bottom: 2px solid white !important;
        }
      }
    }
    .el-container{
      .el-aside{
        padding:0 20px;
        width:100px !important;
      }
    }
  }
</style>
