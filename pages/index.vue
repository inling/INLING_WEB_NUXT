<template>
    <div id="index">
      <el-row>
        <el-col :sm="24" :md="18" class="cards">
          <el-row class="program_m">
            <el-col :span="24">
              <program-frame :banners="banners"></program-frame>
            </el-col>
          </el-row>
          <el-row class="music_m">
            
          </el-row>
        </el-col>
        <el-col :md="6" class="hidden-md-and-down miscellaneous">
          <el-row>
            <el-col :span="24">
              <el-select
                v-model="value"
                multiple
                filterable
                allow-create
                default-first-option
                placeholder="请选择文章标签"
                size="medium">
                <el-option
                  v-for="item in articleOptions"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
                </el-option>
              </el-select>
            </el-col>
            <el-col :span="24">
              <div class="searchTag">
                <el-tag size="mini">vuejs</el-tag>
                <el-tag type="success" size="mini">nuxtjs</el-tag>
                <el-tag type="info" size="mini">css</el-tag>
                <el-tag type="warning" size="mini">html</el-tag>
                <el-tag type="danger" size="mini">JavaScript</el-tag>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-card class="box-card" style="margin:10px 0;">
              <div slot="header" class="clearfix">
                <span>相关内容</span>
              </div>
              <div v-for="o in 4" :key="o" class="text item">
                {{'列表内容 ' + o }}
              </div>
            </el-card>
          </el-row>
          <el-row>
            <el-card class="box-card" style="margin:10px 0;">
              <div slot="header" class="clearfix">
                <span>友链</span>
              </div>
              <div v-for="o in 4" :key="o" class="text item">
                {{'列表内容 ' + o }}
              </div>
            </el-card>
          </el-row>
        </el-col>
      </el-row>     
    </div>
</template>

<script>
import programFrame from '@/components/index/program_frame.vue';
import axios from 'axios';
export default {
  async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
    let {data}= await axios.get('http://59.110.242.246:97/banner?type=0');
    console.log(data)
    return {banners:data.banners}
  },
  data(){
    return {
       articleOptions: [{
          value: 'HTML',
          label: 'HTML'
        }, {
          value: 'CSS',
          label: 'CSS'
        }, {
          value: 'JavaScript',
          label: 'JavaScript'
        }],
        value: []
    }
  },
  head(){
    return {
      title:'英灵 | 技术宅，犹豫就会败北',
      meta:[
        {hid:'keywords',name:'keywords',content:'英灵'},
        {hid:'description',name:'description',content:''}
      ]
    }
  },
  components:{
    programFrame
  }
}
</script>

<style lang="scss">
$theme_color:#ffd04b;

#index{
  .cards{
    padding: 0 20px 20px 0;
    @media screen and (max-width:768px){
      padding: 0;
    }
  }
  .miscellaneous{
    padding: 0 20px 0 20px;
    border-left: solid 1px #e6e6e6;
    &>.el-row{
      border-bottom: solid 1px #e6e6e6;
    }
    .searchTag{
      padding:10px 10px 10px 5px;
      .el-tag{
        margin:0 5px 10px 0px;
        cursor: pointer;
      }
    }
    .box-card{
      font-size: 16px;
    }
  }
}
</style>

