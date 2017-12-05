<template>

    <div>  
    <el-table :data="data" border>
        <el-table-column label="表1">
            <el-table-column label="name" prop="brandName"></el-table-column>
            <el-table-column label="letter" prop="letter"></el-table-column>
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
            axios.get('/api/ap/brand/page',{
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