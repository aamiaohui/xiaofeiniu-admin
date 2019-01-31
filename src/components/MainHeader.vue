<template>
  <div class="xfn-main-header">
    <h3 class="xfn-title">{{$store.state.globalSettings.appName}}管理后台</h3>
    <div class="xfn-right">
        当前用户{{$store.state.adminName}}
        <el-button size="mini" type="danger" plain @click="quit">退出</el-button>
    </div>
  </div>
</template>
<script>
    export default {
        methods:{
            quit(){
                //清除用户的登录信息
                this.$store.commit('setAdminName','');
                //跳转回登录
                this.$router.push('/login');
            }
        }
    }
</script>

<style lang="scss">
 $header-height:50px;
    .xfn-main-header {
        background:#DCDFE6;
        border-radius:4px;
        line-height:$header-height;
        height:$header-height;
        padding:0 12px;
        .xfn-title{
            color:#303133;
            float:left;
            margin:0;
        }
    .xfn-right {
        float:right;
    }
    }
</style>