<template>
    <div id="index">
      <el-row>
        <el-col :sm="24" :md="18" class="cards">
            asd
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
                <span>相关文章</span>
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
export default {
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
      title:'英灵 | 技术宅，搬砖改变世界',
      meta:[
        {hid:'keywords',name:'keywords',content:'英灵'},
        {hid:'description',name:'description',content:''}
      ]
    }
  }
}
</script>

<style lang="scss">
#index{
  .cards{
    padding: 20px;
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
  }
}
</style>

