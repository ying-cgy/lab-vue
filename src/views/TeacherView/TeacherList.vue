<template>
        <ul v-for="(item,i) in teacher" :key="i" style="margin-top:50px">
        <el-row>
            <el-col :xs="24" :sm="24" :md="6" :lg="6" :xl="6"><el-image
                style="width: 100px; height: 100px"
                :src="getImg(i)"
                :initial-index="4"
                fit="cover"/></el-col>
            <el-col :xs="24" :sm="24" :md="18" :lg="18" :xl="18">
                <div class="inf">
                    <li style="font-size:15px">{{item.name}}</li>
                    <li style="font-size:15px">{{item.tel}}</li>
                    <li style="font-size:15px">{{item.email}}</li>
                    <li style="font-weight:bold;font-size:15px">工作经历:</li>
                    <ul v-for="(workitem,j) in data[i]" :key="j" style="padding-left:0px">
                        <li><span>{{workitem.wtime}}</span><span>--</span><span>{{workitem.wetime}}</span></li>
                        <li>{{workitem.companyname}}</li>
                        <li>{{workitem.wdesc}}</li>
                    </ul>
                    <li style="font-weight:bold;font-size:15px">教育经历:</li>
                    <ul v-for="(workitem,j) in edu[i]" :key="j" style="padding-left:0px">
                        <li><span>{{workitem.wtime}}</span><span>--</span><span>{{workitem.wetime}}</span></li>
                        <li>{{workitem.companyname}}</li>
                        <li>{{workitem.wdesc}}</li>
                    </ul>
                    <li style="font-weight:bold;font-size:15px">个人荣誉:</li>
                    <ul v-for="(workitem,j) in honor[i]" :key="j" style="padding-left:0px">
                        <li><span>{{workitem.wtime}}</span><span>--</span><span>{{workitem.wetime}}</span></li>
                        <li>{{workitem.companyname}}</li>
                        <li>{{workitem.wdesc}}</li>
                    </ul>
                    <li style="font-weight:bold;font-size:15px">参与项目:</li>
                    <ul v-for="(workitem,j) in pro[i]" :key="j" style="padding-left:0px">
                        <li><span>{{workitem.wtime}}</span><span>--</span><span>{{workitem.wetime}}</span></li>
                        <li>{{workitem.companyname}}</li>
                        <li>{{workitem.wdesc}}</li>
                    </ul>
                    <li style="font-weight:bold;font-size:15px">发表:</li>
                    <ul v-for="(workitem,j) in publish[i]" :key="j" style="padding-left:0px">
                        <li><span>{{workitem.wtime}}</span><span>--</span><span>{{workitem.wetime}}</span></li>
                        <li>{{workitem.companyname}}</li>
                        <li>{{workitem.wdesc}}</li>
                    </ul>
                </div>
            </el-col>   
        </el-row>
        </ul>
</template>
<script>
import request from '@/utils/request'
export default {
    name:'HomeView',
    data(){
        return{
            teacher:[],
            work:[],
            edu:[],
            honor:[],
            pro:[],
            publish:[],
            data:[]
        }
    },
    created(){
        this.load();
    },
    methods:{
        load(){
            var i=this.$route.query.index;
            request.get("/user",{
                params:{
                pageNum:1,
                pageSize:30,
                search:'',
                }
            }).then(res=>{
                console.log(res)
                this.teacher=res.data.records;
                
            });
            request.get("/workExp").then(res=>{
                console.log(res)
                this.work=res.data;
                console.log(this.work)
                for(var i=0;i<this.teacher.length;i++){
                    var list=[],eduL=[],horL=[],proL=[],pubL=[]
                    var k=0;
                    for(var j=k;j<this.work.length;j++){
                        if(this.work[j].tid>this.teacher[i].id){
                            break;
                        }else if(this.work[j].tid==this.teacher[i].id){
                            if(this.work[j].type==1){
                                list.push(this.work[j])
                            }else if(this.work[j].type==2){
                                eduL.push(this.work[j])
                            }else if(this.work[j].type==3){
                                horL.push(this.work[j])
                            }else if(this.work[j].type==4){
                                proL.push(this.work[j])
                            }else if(this.work[j].type==5){
                                pubL.push(this.work[j])
                            }
                        }
                    }
                    k=j;
                    this.data.push(list)
                    this.edu.push(eduL)
                }
                console.log(this.data)
                console.log(this.edu)
            })
        },
        getImg(i){
          return this.teacher[i].photo
        },
        dataTrans(data){
          data=data.split("T")[0];
          console.log(data)
          return data
        },
    }
    
}
</script>
<style>
.image{
    width: 50%;
}
ul{
list-style-type:none;
}
ul li{
    padding-top: 10px;
    padding-bottom: 10px;
    word-break: break-word;
}
/* ul li:hover{
    color: rgb(0, 102, 211);
    cursor:pointer;
} */
</style>