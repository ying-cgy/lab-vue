<template>
    <ul class="context">
        <li class="infinite-list-item">
            <h3 class="contexta">{{list.name}}</h3>
            <li style="padding-bottom:5px;margin-bottom:10px;font-size: small;border-bottom: 1px solid #ccc;">{{dataTrans(list.data)}}</li>
            <li style="padding-bottom:20px"><span class="cen_data">{{list.context}}</span></li>
            <img :src="getImg()" style="width:80%;display:inline">
        </li>
    </ul>
</template>
<style>
.context{
  list-style-type:none;
  /* padding-left: 100px; */
}
.context>li{
    margin-right:10px;
    padding-bottom: 10px;
    min-width: cal(100vh-300px);
}
/* .contexta{
    overflow: hidden;
} */
.cen_data{
    /* float: right; */
    color:rgb(121, 121, 121);
    font-size: small;
}
</style>
<script>
import request from '@/utils/request'
export default {
    name:'HomeView',
    data(){
        return{
            list:""
        }
    },
    created(){
        this.load();
    },
    methods:{
        fix(num, length) {
            return ('' + num).length < length ? ((new Array(length + 1)).join('0') + num).slice(-length) : '' + num;
        },
        load(){
            var i=this.$route.query.index;
            request.get("/",{
                params:{
                pageNum:1,
                pageSize:30,
                search:'',
                id:i
                }
            }).then(res=>{
                console.log(res)
                this.list=res.data;
            });
        },
        getImg(){
          return this.list.cover
        },
        dataTrans(data){
          data=data.split("T")[0];
          console.log(data)
          return data
        }
    }
    
}
</script>
