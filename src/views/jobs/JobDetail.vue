<template>
  
  <div v-if="jobly">
  <p>My title is - {{jobly.title}}</p>
  <p>My id is - {{jobly.id}}</p>
  <p>My detail is - {{jobly.detail}}</p>
  </div>
  
  
</template>

<script>
export default {

  // props:['id'],
  data(){
    return{
      ids:this.$route.params.id,
      jobly:null
    }
  },
  mounted(){
    fetch('http://localhost:3000/jobs/'+this.ids)
    .then((response)=>{
      return response.json();
    })
    .then((data)=>{
      this.jobly=data;
    })
    .catch((err)=>{
      console.log(err);
    })
  }
  
}
</script>

<style>

</style>