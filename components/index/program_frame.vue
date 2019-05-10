<template>
  <div id="program_frame">
    <el-tabs v-model="activeName">
      <el-tab-pane label="技术文章" name="first">
        <span slot="label">
          <i class="icon icon_t program_icon"></i>
          技术文章
        </span>
        技术文章
      </el-tab-pane>
      <el-tab-pane label="配置管理" name="second">配置管理</el-tab-pane>
      <el-tab-pane label="角色管理" name="third">角色管理</el-tab-pane>
      <el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
    </el-tabs>
    <p class="frame_name">
      <i class="icon icon_t program_icon"></i>
      技术文章
    </p>
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>卡片名称</span>
      </div>
      <div v-for="o in 4" :key="o" class="text item">
        <el-card class="box-card">
           <div v-for="o in 4" :key="o" class="text item">
             {{o}}
            </div>
        </el-card>
      </div>
    </el-card>
  </div>
</template>

<script>
export default {
  data(){
    return {
      activeName:''
    }
  }
}
</script>

<style lang="scss">
.frame_name{
  font-size: 20px;
  line-height: 20px;
  font-weight: 400;
  margin-right: 20px;
  color: #222;
  margin:0 0 20px 0;
  position: relative;
}
  .program_icon{
    background-position: -141px -780px;
    margin-bottom:10px;
  }
</style>

