<template>
  <div class="">
    <h1>菜品列表</h1>
     <el-tabs  type="border-card">
         <el-tab-pane v-for="(category,i) in dishList" >
          <span slot="label">
            <el-badge :value="category.dishList.length">{{category.cname}}</el-badge>
          </span>

          <el-row>
            <el-col v-for="(d,j) in category.dishList" :xs="12" :md="6" :lg="4" :xl="3">
             <!---->
             {{d.title}}
             <img :src="require('../assets/img/dish/'+d.imgUrl)" alt="" style="max-width:100%"></img>
            </el-col>          
          </el-row>
          </el-tab-pane>
        </el-tabs>
  </div>
</template>
<script>
 export default {
   data(){
     return {
       dishList:[]  //[{cid:X,cname:x,dishList:[]}]
     }
   },
   mounted(){
     //异步获取菜品列表
     var url = this.$store.state.globalSettings.apiUrl + '/admin/dish';
     this.$axios.get(url).then(({data})=>{
       this.dishList = data;
     }).catch((err)=>{
       console.log(err);
     })
   }
 }
</script>
