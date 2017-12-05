<template>

    <div>  
    <el-table :data="data" border>
        <el-table-column label="carBrand">
            <el-table-column label="carBrandName" prop="carBrandName"></el-table-column>
            <el-table-column label="stateName" prop="stateName"></el-table-column>
        </el-table-column>
    </el-table>
    <el-input v-model="brandName"></el-input>
    <el-button @click="query">search</el-button>
    </div> 

</template>    

<script>
import axios from 'axios';
export default {
    data(){
        return {
            data:[
                {
                    
                }
            ],
            brandName:''
        }
    },

    methods:{
        query(){
            axios.get('/api/ap/car/brand/list',{
                params:{
                    brandName: this.brandName
                }
            }).then(res=>{
                if(res.data.success){
                    this.data = res.data.data;
                }else {

                }
            }).catch()
        }
    },

    created(){
        // this.query();
    }
    
}


</script>