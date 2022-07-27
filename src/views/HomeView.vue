<template>
  <!-- <div class="carousel">
    <el-carousel :interval="5000">
      <el-carousel-item v-for="item in 6" :key="item">
        <h3 text="2xl" justify="center">{{ item }}</h3>
      </el-carousel-item>
    </el-carousel>
  </div> -->
  <el-row>
      <el-col :xs="24" :sm="24" :md="17" :lg="17" :xl="17">
        <div>
          <dt style="padding-left:46px;padding-right: 10px;">
            <p style="float:left;font-size: 25px;margin-bottom:0px;margin-top:10px;">news</p>
            <p style="float:right;margin-bottom:0px;margin-top: 22px;" class="more" @click="more()">more</p>
          </dt>
          
          <ul class="left">
              <li v-for="(item,i) in list" :key="i" class="infinite-list-item">
                  <h3 class="a"  @click="newsInf(item.id)">{{item.name}}</h3>
                  <a style="float:left;width:190px"><img :src="getImg(i)" style="width:80%;display:inline"></a>
                  <dt>{{dataTrans(item.data)}}</dt>
                  <dt style="padding-top:20px">{{item.descri}}</dt>
              </li>
          </ul>
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :md="7" :lg="7" :xl="7" style="padding-left:10px">
        <div>
          
          <dt style="padding-left:46px;padding-right: 10px;">
            <p style="float:left;font-size: 15px;margin-bottom:0px;margin-top:15px;">publications</p>
            <p style="float:right;margin-bottom:2px;margin-top: 18px;" class="more" @click="morei()">more</p>
          </dt>
          
          <ul class="right">
            <el-row>
              <li v-for="(item,i) in list" :key="i" class="infinite-list-item">
                  <a style="float:left;width:190px;padding-top: 10px;"><img :src="getImg(i)" @click="morei()" style="width:80%;display:inline"></a>
              </li>
            </el-row>
          </ul>
        </div>
      </el-col>
  </el-row>
</template>

<style scoped>
.left{
list-style-type:none;
padding-top: 45px;
}
.right{
  padding-top: 50px;
list-style-type:none;
}
.left>li{
    margin-right:10px;
    padding-left: 10px;
    padding-top: 10px;
    padding-bottom: 100px;
    border-top: 1px solid #ccc;
}
.a:hover{
    color: rgb(0, 102, 211);
    cursor:pointer;
}
.a{
    overflow: hidden;
}
.more:hover{
  color: rgb(0, 102, 211);
  cursor:pointer;
}
/* .carousel{
  margin-top: 50px;
}

.el-carousel__item h3 {
  color: #475669;
  opacity: 0.75;
  line-height: 200px;
  margin: 0;
  text-align: center;
}

.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #d3dce6;
} */
</style>

<script>

import request from '@/utils/request'
export default {
    name:'HomeView',
    data(){
        return{
            list:[],
            imgUrl:''
        }
    },
    created(){
        this.load();
    },
    methods:{
        load(){
            request.get("/",{
                params:{
                pageNum:1,
                pageSize:10,
                search:''
                }
            }).then(res=>{
                console.log(res);
                this.list=res.data.records;
            });
        },
        getImg(i){
          return this.list[i].cover
        },
        newsInf(id){
          this.$router.push({path: '/news',query:{ index:id}});
        },
        dataTrans(data){
          data=data.split("T")[0];
          console.log(data)
          return data
        },
        more(){
          this.$router.push({path: '/newsA'});
        },
        morei(){
          this.$router.push({path: '/publication'});
        }
    }
    
}
</script>
