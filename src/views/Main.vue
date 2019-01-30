<template>
  <div class="main">
    <el-container>
      <!--左侧的菜单栏-->
        <el-aside style="width:200px">左边边栏</el-aside>
        <el-container>
        <!--顶部的信息栏-->
        <el-header style="height:60px">顶部栏</el-header>
        <!--主体部分-->
        <el-main>
         <router-view></router-view>
        </el-main>
        </el-container>
    </el-container>
  </div>
</template>
<script>
   export default {
     //create/mounte/uodate/destory
     beforeCreate(){
       //main组件创建之前要先检查是否已经登录为管理员
       if(!this.$store.state.adminName){
         this.$router.push('/login');//未登录跳转
       }
     }
   }
</script>
