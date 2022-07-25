<template>
  <div >
    <el-menu
      :default-active="activeIndex"
      class="el-menu-demo"
      mode="horizontal"
      :ellipsis="false"
      @select="handleSelect"
    >
      <el-menu-item index="0"><img src="@/assets/logo.png" style="width:50px"></el-menu-item>
      <div class="flex-grow" />
      <router-link to="/">
        <el-menu-item index="1" >home</el-menu-item>
      </router-link>
      <router-link to="/newsA">
        <el-menu-item index="2">infrom</el-menu-item>
      </router-link>
      <router-link to="/user">
        <el-menu-item index="3" >teacher</el-menu-item>
      </router-link>
      <router-link to="/publication">
        <el-menu-item index="4" >publication</el-menu-item>
      </router-link>
    </el-menu>
    <p style="padding-left:20px;height:60px;background-color:#1359b6;margin:0 0 0 0;color: white;font-size: 40px;">welcome to our lab</p>
  </div>
</template>
<script>
import { ref } from 'vue'

// const activeIndex = ref('1')
// const handleSelect = (key: string, keyPath: string[]) => {
//   console.log(key, keyPath)
// }
export default {
  name: 'HomeView',
  components: {
  },
  data(){
    return{
      search:'',
      activeIndex:"1"
    }
  },
  methods:{
    // home(){
    //   this.$router.push({path: '/');
    // },
    // inform(){
    //   this.$router.push({path: '/newsA');
    // },
    // teacher(){
    //   this.$router.push({path: '/user');
    // },
    // pub(){
    //   this.$router.push({path: '/publication');
    // }
    // load(){
    //   request.get("/user",{
    //     params:{
    //       pageNum:this.currentPage,
    //       pageSize:this.pageSize,
    //       search:this.search
    //     }
    //   }).then(res=>{
    //     console.log(res);
    //     this.tableData=res.data.records;
    //     this.total=res.data.total;
    //   });
    // }

  }
}

</script>
<style>
.flex-grow {
  flex-grow: 1;
}
</style>