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
        <el-menu-item index="1" style="padding-left:10px;padding-right:10px">home</el-menu-item>
      </router-link>
      <router-link to="/newsA">
        <el-menu-item index="2" style="padding-left:10px;padding-right:10px">infrom</el-menu-item>
      </router-link>
      <router-link to="/user">
        <el-menu-item index="3" style="padding-left:10px;padding-right:10px">teacher</el-menu-item>
      </router-link>
      <router-link to="/publication">
        <el-menu-item index="4" style="padding-left:10px;padding-right:10px">publication</el-menu-item>
      </router-link>
    </el-menu>
    <p style="padding-left:20px;height:60px;background-color:#1359b6;margin:0 0 0 0;color: white;font-size: 40px;">welcome to our lab</p>
  </div>
</template>
<script>
import { ref } from 'vue'

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
    handleSelect(key){
      this.activeIndex=key
    }

  }
}

</script>
<style>

.flex-grow {
  flex-grow: 1;
}
</style>