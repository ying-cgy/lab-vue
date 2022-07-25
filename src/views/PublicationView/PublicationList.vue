<template>
    <ul class="context">
        <li style="border-bottom:1px solid #ccc"><h2>Publication</h2></li>
        <li v-for="(item,i) in list" :key="i" class="infinite-list-item" style="margin-top:10px">
            <li>{{item.proname}}</li>
            <!-- <li>{{item.ptime}}</li> -->
            <div style="text-align:center"><img :src="getImg(i)" style="width:70%;display:inline;margin-top:10px;"></div>
        </li>
    </ul>
    <div style="margin:10px">
      <el-pagination
        :currentPage="currentPage"
        :page-size="pageSize"
        :page-sizes="[5, 10, 15, 20]"
        :small="small"
        :disabled="disabled"
        :background="background"
        layout="total, sizes, prev, pager, next, jumper"
        :total="total"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
      /></div>
</template>
<style>
li{
    list-style-type:none;
}
</style>
<script>
import request from '@/utils/request'
export default {
    name:'HomeView',
    data(){
        return{
            list:[],
            currentPage:1,
            pageSize:20,
            total:0,
        }
    },
    created(){
        this.load();
    },
    methods:{
        load(){
            var i=this.$route.query.index;
            request.get("/publications",{
                params:{
                pageNum:this.currentPage,
                pageSize:this.pageSize,
                search:this.search
                }
            }).then(res=>{
                console.log(res)
                this.list=res.data.records;
                this.total=res.data.total;
            })
        },
        getImg(i){
          return this.list[i].cover
        },
        dataTrans(data){
          data=data.split("T")[0];
          console.log(data)
          return data
        },
        handleSizeChange(val){
            this.pageSize=val
            this.load()
            console.log(`${val} items per page`)
        },
            handleCurrentChange(val){
            this.currentPage=val
            this.load()
            console.log(`current page: ${val}`)
        },
    }
    
}
</script>
