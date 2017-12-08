<template>

    <div> 
        <el-row :gutter="10" align="center"> 
            <el-col :span="8">
                <el-button v-show="true">1111</el-button>
            </el-col>
            <el-col :span="8">
              <el-input v-model="carBrandName" placeholder="请输入内容" width="150" align="center"/>
            </el-col>
         </el-row>
         <el-row :gutter="10"> 
            <el-col :span="8">
              <el-button @click="query">查询</el-button>
            </el-col>
            <el-col :span="8">
              <el-button @click="insertDlgshow=true">新增</el-button>
            </el-col>
        </el-row>
        
        <el-table :data="data" border>
            <el-table-column label="carBrand" align="center">
                <el-table-column label="操作">
                    <template scope="scope">
                        <el-button @click="edit(scope.row.carBrandId)"></el-button>
                    </template>    
                </el-table-column>
                <el-table-column label="carBrandName" prop="carBrandName" align="left"></el-table-column>
                <el-table-column label="stateName" prop="stateName" align="left"></el-table-column>
                <el-table-column label="createTime" prop="createTime" align="left"></el-table-column>
                <el-table-column label="carBrandCode" prop="carBrandCode" align="left"></el-table-column>
            </el-table-column>
        </el-table>
        
        <el-dialog title="插入品牌" :visible.sync="insertDlgshow">
            <addBrand></addBrand>
        </el-dialog>

        <el-dialog title="修改品牌" :visible.sync="editDlgshow">
            <editBrand :id="editId" :key="editId"></editBrand>
        </el-dialog>
    </div> 

</template>    

<script>
import axios from 'axios';
import addBrand from './addBrand.vue';
import editBrand from './editBrand.vue';
export default {
    data(){
        return {
            data:[
                {
                    
                }
            ],
            carBrandName:'',
            insertDlgshow:false,
            editDlgshow:false,
            editId:''
        }
    },

    methods:{
        query(){
            axios.get('/api/ap/car/brand/list',{
                params:{
                    carBrandName: this.carBrandName
                }
            }).then(res=>{
                if(res.data.success){
                    this.data = res.data.data;
                }else {

                }
            }).catch()
        },
        edit(id){
            this.editDlgshow = true;
            this.editId = id;
        }
    },

    components:{
      addBrand,
      editBrand
    },

    created(){
        this.query();
    }
    
}


</script>