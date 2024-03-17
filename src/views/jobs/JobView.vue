<template>
  <h1>Jobs Types</h1>
  <div v-for="job in jobs" :key="job.id" class="color">
    <router-link :to="{name:'jobDetail',params:{id:job.id}}">
        <p>{{job.title}}</p>
    </router-link>
  </div>
</template>

<script>
export default {
    data(){
        return{
            jobs:[]
                // {id:"1", title:"project manager", detail:"creative coder project manager"},
                // {id:"2", title:"designer", detail:"creative coder designer"},
                // {id:"3", title:"developer", detail:"creative coder developer"},
            
        }
    },
   mounted(){
    fetch('http://localhost:3000/jobs')
    .then((response)=>{
        return response.json()
    })
    .then((datas)=>{
        this.jobs=datas;
    })
    .catch((err)=>{
        console.log(err);
    })
   }

}
</script>

<style>
    .color{
        color: blueviolet;       
    }
</style>