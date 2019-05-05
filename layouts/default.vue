<template>
  <el-container class="default">
    <el-header>
      <el-menu :default-active="activeIndex" 
                active-text-color="#ffd04b" 
                class="el-menu-demo" 
                mode="horizontal"
                :router="true">
        <el-menu-item
          v-for="(item,i) in navMenu" 
          :key="i" 
          :index="item.index">{{item.label}}</el-menu-item>
        
        <!--终极缩小下拉菜单/联系方式、分享链接-->
        <el-dropdown trigger="click" class="share">
          <span class="el-dropdown-link">
            <i class="el-icon-share"></i>
          </span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>QQ</el-dropdown-item>
            <el-dropdown-item>微博</el-dropdown-item>
            <el-dropdown-item>Twitter</el-dropdown-item>
            <el-dropdown-item>Github</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>

        <!--终极缩小下拉菜单/主菜单-->
        <el-dropdown trigger="click" class="hidden-sm-and-up">
          <span class="el-dropdown-link">
            <i class="el-icon-menu"></i>
          </span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>编程技术</el-dropdown-item>
            <el-dropdown-item>时间线</el-dropdown-item>
            <el-dropdown-item>音乐</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>


        <!--单选组-->
        <el-radio-group v-model="share" size="mini"  fill="#ffd04b" class="hidden-sm-and-down">
          <el-radio-button label="QQ"></el-radio-button>
          <el-radio-button label="微博"></el-radio-button>
          <el-radio-button label="Twitter"></el-radio-button>
          <el-radio-button label="Github"></el-radio-button>
        </el-radio-group>

        <!--语言-->
        <el-select v-model="lang" size="mini">
          <el-option v-for="item in langList" 
                    :key="item.index" 
                    :label="item.label" 
                    :value="item.value"></el-option>
        </el-select>
        
        <!--搜索栏-->
        <el-input
          v-model="searchInfo"
          placeholder="搜索"
          prefix-icon="el-icon-search"
          size="mini"
          class="search">
        </el-input>

      </el-menu>
    </el-header>
    <el-container>
      <el-aside class="left">
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
        share:'QQ',
        navMenu:[
          {index:'/',label:'英灵'},
          {index:'/program',label:'编程技术'},
          {index:'/timeline',label:'时间线'},
          {index:'/music',label:'音乐'},
        ],

        /**语言 */
        lang:'chinese',
        langList:[
          {index:1,label:'中文',value:'chinese'},
          {index:2,label:'English',value:'english'},
        ],

        /**搜索信息 */
        searchInfo:'',
        shareTag:[
          {}
        ]
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
  $theme_color:#ffd04b;

  .el-container.default{
    min-width: 361px;
    .el-header{
      .el-menu--horizontal {
        .el-menu-item{
          &:first-child{
            color:$theme_color;
            font-size: 30px;
            font-family: 'Night';
          }
          &:not(.is-disabled):hover{
            outline: 0;
            color: $theme_color;
          }
        }
        &>.el-menu-item.is-active{
          border-bottom: 2px solid white !important;
        }
        @media screen and (max-width:768px){
          .el-menu-item:not(:first-child){
            display: none;
          }
        }
      }


      /*终极缩小*/
      .el-dropdown{
        float:right;
        padding:15px 0 20px;
        height:60px;
        span{
          font-size:30px;
          color:$theme_color;
        }
        &:focus{
          outline: 0;
        }
        .el-dropdown-link:focus {
          outline: 0;
        }
        &.share{
          @media screen and (min-width:991px){
            display: none;
          }
        }
      }


      /*联系方式*/
      .el-radio-group{
        float:right;
        padding:20px;
        height:60px;
        .el-radio-button__inner {
          &:hover{
            color: $theme_color;
          }
        }
        &:focus{
          outline:0;
        }
      }

      /*选择语言*/
      .el-select{
        float:right;
        padding:20px;
        height:60px;
        width:150px;
        .el-input.is-focus{
          .el-input__inner {
            border-color: $theme_color;
          }
        }
        .el-input__inner{
          &:focus{
            border-color: $theme_color;
          }
        }
        &:focus{
          outline:0;
        }
      }
      
      
      .el-input.search{
        float:right;
        padding:20px;
        height:60px;
        width:160px;
        .el-input__prefix {
          left: 25px;
          top: 3px;
        }
        .el-input__inner:focus {
            border-color: $theme_color;
            outline: 0;
        }
        @media screen and (max-width:768px){
            display:none;
        }
      }
    }
    .el-container{
      .el-aside.left{
        padding:0 20px;
        width:100px !important;
      }
      @media screen and (max-width:768px){
        .el-aside{
          display:none;
        }
      }
    }
  }


  .el-select-dropdown{
    .el-select-dropdown__item.selected{
      color:$theme_color;
    }
  }

  .el-dropdown-menu{
    .el-dropdown-menu__item:not(.is-disabled):hover {
      background-color: #ecf5ff;
      color: $theme_color;
    }
  }
</style>
