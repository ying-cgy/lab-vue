<template>
  <div class="cardInf">
    <el-row>
        <el-col :span="22">
            <!-- <el-card shadow="always">  -->
                <el-row>
                    <el-col :xs="24" :sm="24" :md="12" :lg="12" :xl="12"><img :src="imgUrl" style="width:95%"></el-col>
                    <el-col :xs="24" :sm="24" :md="12" :lg="12" :xl="12" style="padding-left:10px"><span>支撑和简单介绍  这里为了凑字数  凑字出，凑字数asasaasasasa   </span></el-col>
                </el-row>
                <router-link to="/user">
                    <a>know more</a>
                </router-link>
                
            <!-- </el-card> -->
        </el-col>
    </el-row>
    <el-row style="margin-top:20px">
        <el-col :span="22">
            <!-- <el-card shadow="always">  -->
                <dl>
                    <dt>title</dt>
                    <dt>desc</dt>
                    <dt>tel</dt>
                    <dt><a>email</a></dt>
                </dl>
            <!-- </el-card> -->
        </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.cardInf{
    padding-top: 50px;
    
}
</style>

<script>

export default {
  name: 'HomeView',
  components: {
  },
  data(){
      return{
          imgUrl:require('@/assets/people.png')
      }
  }
}
</script>
