<template>
  <div id="program_frame">
    <el-carousel :interval="4000" :height="bannerHeight+'px'" indicator-position="none" class="b1">
      <el-carousel-item v-for="(item,i) in banners" :key="i">
        <img ref="bannerHeight" :src="item.imageUrl" alt="" @load="imgLoad">
      </el-carousel-item>
    </el-carousel>
    <el-tabs v-model="activeName">
      <el-tab-pane label="技术文章" name="first">
        <span slot="label">
          <i class="icon icon_t program_icon"></i>
          技术文章
        </span>
        <el-row>
          <el-col :lg="4"  :sm="8" :xs="12" v-for="o in 6" :key="o">
            <el-card :body-style="{ padding: '0px' }">
              <img src="http://p1.music.126.net/Iq2JcHdrZvdt2Ekw7nN1kA==/109951163912213947.jpg?param=140y140" class="image">
              <div style="padding: 14px;">
                <div class="bottom clearfix">
                  <time class="time">{{ 1 }}</time>
                  <el-button type="text" class="button">操作按钮</el-button>
                </div>
              </div>
            </el-card>
          </el-col>
        </el-row>
      </el-tab-pane>
      <el-tab-pane label="音乐" name="second">
        <span slot="label" id="qwe">
          音乐
        </span>
        音乐
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
  .time {
    font-size: 13px;
    color: #999;
  }
  
  .bottom {
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
      display: table;
      content: "";
  }
  
  .clearfix:after {
      clear: both
  }

  #qwe:focus {
    outline: none;
  }
</style>

