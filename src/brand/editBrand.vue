<template>
<div>
<el-form :model="frmInsert">
        <el-form-item label="carBrandName">
            <el-input v-model="frmInsert.carBrandName"></el-input>
        </el-form-item>
        <el-form-item label="carBrandCode">
            <el-input v-model="frmInsert.carBrandCode"></el-input>
        </el-form-item>
    </el-form>
    <el-button @click="save">提交</el-button>
</div>
    
</template>
<script>
import axios from 'axios';
export default {
    props:{
        id:String
    },
    data(){
        return {
            frmInsert:{
                carBrandName:'',
                carBrandCode:''
            }
        }
    },
    methods:{
        save(){
            axios.post('/api/ap/car/brand/update',this.frmInsert).then(res=>{

            }).catch(error=>{

            })
        }
    },
    mounted(){
        axios.get('/api/ap/car/brand/get/'+this.id).then(res=>{
            this.frmInsert = res.data.data
        }).catch(error=>{

        })
    },
    watchs:{
       'id':function(newId,oldId){
           axios.get('/api/ap/car/brand/get/'+this.id).then(res=>{
            this.frmInsert = res.data.data
        }).catch(error=>{

        })
       }
    }
}

</script>
