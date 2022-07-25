<template>
    <ul class="left">
        <li v-for="(item,i) in list" :key="i" class="infinite-list-item" @click="newsInf(item.id)">
            <a class="a">{{item.name}}</a>
            <span style="float:right">{{dataTrans(item.data)}}</span>
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
      />
    </div>
</template>
<script>
import request from '@/utils/request'
export default {
    name:'Aside',
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
            request.get("/",{
                params:{
                pageNum:this.currentPage,
                pageSize:this.pageSize,
                search:this.search
                }
            }).then(res=>{
                console.log(res);
                this.list=res.data.records;
                 this.total=res.data.total;
            });
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
        dataTrans(data){
          data=data.split("T")[0];
          console.log(data)
          return data
        },
        newsInf(id){
          this.$router.push({path: '/news',query:{ index:id}});
        },
    }
    
}
</script>
<style>
.left{
list-style-type:none;
}
.left>li{
    margin-right:10px;
    padding-left: 10px;
    padding-top: 10px;
    padding-bottom: 10px;
    border-bottom: 1px solid #ccc;
}
.left>li:hover{
    color: rgb(0, 102, 211);
    cursor:pointer;
}
.a{
    padding-left:10px;
    overflow: hidden;
}
</style>