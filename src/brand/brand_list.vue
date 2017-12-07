<template>

    <div> 
    <el-input v-model="carBrandName" size="large"/>
    <el-button @click="query">search</el-button>
    <el-button @click="show=true">insert</el-button>
    
    <el-table :data="data" border>
        <el-table-column label="carBrand" align="center">
            <el-table-column label="carBrandName" prop="carBrandName" align="left"></el-table-column>
            <el-table-column label="stateName" prop="stateName" align="left"></el-table-column>
            <el-table-column label="createTime" prop="createTime" align="left"></el-table-column>
            <el-table-column label="carBrandCode" prop="carBrandCode" align="left"></el-table-column>
        </el-table-column>
    </el-table>
    <el-dialog title="插入品牌" :visible.sync="show">
        <addBrand></addBrand>
    </el-dialog>
    </div> 

</template>    

<script>
import axios from 'axios';
import addBrand from './addBrand.vue';
export default {
    data(){
        return {
            data:[
                {
                    
                }
            ],
            carBrandName:'',
            show:false,
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
        }
    },

    components:{
      addBrand
    },

    created(){
        this.query();
    }
    
}


</script>