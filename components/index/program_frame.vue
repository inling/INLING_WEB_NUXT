<template>
  <div id="program_frame">
    <p>技术文章</p>
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

    }
  }
}
</script>

<style lang="scss">

</style>

