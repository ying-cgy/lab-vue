<template>
  <nav>
    <div class="center">
      <el-affix :offset="0">
        <news></news>
      </el-affix>
    </div>
    <div>
        <el-row >
          <el-col :xs="24" :sm="24" :md="2" :lg="2" :xl="1"><div class="grid-content bg-purple"/></el-col>
          <el-col :xs="24" :sm="24" :md="5" :lg="5" :xl="6"><el-affix :offset="130"><Aside></Aside></el-affix></el-col>
          <el-col :xs="24" :sm="24" :md="15" :lg="15" :xl="16" ><router-view style="flex:1"/></el-col>
          <el-col :xs="24" :sm="24" :md="2" :lg="2" :xl="1"><div class="grid-content bg-purple-light"/></el-col>
        </el-row>
    </div>
  </nav>
  <!-- <router-view/> -->
</template>
<script>
import news from "./components/news.vue";
import Aside from "./components/Aside.vue";
export default {
  name:"Layout",
  components:{
    news,
    Aside
}
}
</script>
<style>
/* .center{
  min-width: 100vh;
} */
/* .right{
  border-left: 1px solid #ccc;
  position:absolute;
  left:340px;
  min-height:calc(100vh - 67px);
  width:900px;
} */
/* .center{
  display:flex;
  text-align: center;
  justify-content: center;
  margin-left: 200px;
  margin-right: 200px;
  border-bottom: 2px solid rgb(61, 61, 61);
}
.left{
  position:absolute;
  top:390px;
  left:200px;
}
.right{
  border-left: 1px solid #ccc;
  position:absolute;
  top:390px;
  left:400px;
  min-height:calc(100vh) 
  min-height:calc(100vh - 390px) 
} */
</style>
