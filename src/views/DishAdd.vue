<template>
  <div class="xfn-dish">
    <h1>添加菜品</h1>
    <el-form label-width="100px">
      <el-form-item label="菜品图片：">
        <el-upload class="xfn-uploader" :action="uploadAction" :on-success="doUploadSucc" name="dishImg">
         <img v-if="imageUrl" :src="imageUrl" class="avatar">
         <i v-else class="el-icon-plus avatar-uploader-icon"></i>
        </el-upload>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
  export default {
    data(){
      return {
        imageUrl:'',
        uploadAction:
        this.$store.state.globalSettings.apiUrl + '/admin/dish/image',
        formData:{
          title:'',
          imgUrl:'',  //菜品图片在服务器上的随机文件名
          price:'',
          detail:'',
          categoryId:''
        }
      }
    },
    methods:{
      doUploadSucc(res,file){
        //文件上传成功后客户端得到响应消息后的处理函数
        //res：服务器端返回的响应消息
        //file：从INPUT[type=file]中读取的第一个上传的文件对象
        console.log(res);
        this.formData.imgUrl = res.fileName;
        this.imageUrl = URL.createObjectURL(file.raw);
        //把上传的文件
      }
    }
  }
</script>
<style lang="scss">
  .xfn-uploader{
    .el-upload{
      border:1px dotted #aaa;
      border-radius:3px;
      cursor:pointer;
      width:250px;
      height:177px;
      overflow:hidden;
      &:hover{
        border-color:#409eff;
      }
      .avatar-uploader-icon {
        font-size: 28px;
        color: #8c939d;
        width: 178px;
        height: 178px;
        line-height: 178px;
        text-align: center;
      }
      .avatar {
        width: 100%;
        height: 178px;
        display: block;
      }
      .img{
        max-height:100%;
      }
        }
  }
</style>