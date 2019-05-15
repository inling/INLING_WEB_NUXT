<template>
  <div id="program_frame">
    <el-carousel :interval="4000" type="card" :height="bannerHeight+'px'" indicator-position="none" class="b1">
      <el-carousel-item v-for="(item,i) in banners" :key="i">
        <img ref="bannerHeight" :src="item.picUrl" alt="" @load="imgLoad">
      </el-carousel-item>
    </el-carousel>
    <el-tabs v-model="activeName">
      <el-tab-pane label="技术文章" name="first">
        <span slot="label">
          <i class="icon icon_t program_icon"></i>
          技术文章
        </span>
        技术文章
      </el-tab-pane>
    </el-tabs>
    
    <el-tabs v-model="activeName">
      <el-tab-pane label="音乐" name="first">
        <span slot="label">
          <i class="icon icon_t music_icon"></i>
          音乐
        </span>
        音乐
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
export default {
  data(){
    return {
      activeName:'first',
      bannerHeight:''
    }
  },
  mounted(){
    this.imgLoad();
    window.addEventListener('resize',()=>{
      this.bannerHeight=this.$refs.bannerHeight[0].height;
      this.imgLoad();
    },false);
  },
  methods:{
    imgLoad(){
      this.$nextTick(()=>{
        this.bannerHeight=this.$refs.bannerHeight[0].height;
      })
    }
  },
  props:{
    banners:Array
  }
}
</script>

<style lang="scss">
#program_frame{
  .el-carousel {
    img{
      width: 100%;
    }
  }

  .el-tabs:nth-child(2){
    margin-top:20px;
  } 

  .program_icon{
    background-position: -141px -780px;
    margin-bottom:10px;
  }
 
  .music_icon{
    background-position: -140px -266px;
    margin-bottom:10px;
  }
}

</style>

