<template>

  <div class="jobs">
    <h2>Jobs</h2>
    <div v-if="jobs.length">
        <div class="job" v-for="job in jobs" :key="job.id" >
        <router-link :to="{name:'jobsdetails', params:{id:job.id}}">
            <h3>{{job.title}}</h3>
        </router-link>
        </div>
    </div>
    <div v-else>
    <p>Loading...</p>
    </div>
    <div v-if="error">
        <p>Network Error</p>
    </div>
  </div>
  
</template>

<script>
export default {
    data(){
        return{
            jobs:[],
            error:false
        }
    },
    async created(){
        this.jobs = await this.fetchData();
    },
    methods:{
        async fetchData(){
            const res= await fetch('api/jobs')
            if(res.status===200){
                this.error = false
                const data = await res.json();
                return data
            }else{
                
                this.error=true
            }
        }
    } 
}
</script>

<style>
.job h3{
    background:#f4f4f4;
    padding:20px;
    border-radius: 10px;
    margin:10px auto;
    max-width:600px;
    cursor:pointer;
    color:#444;
}
.job h3:hover{
    background:#ddd;
    
}
.job a{
     text-decoration: none;   
    }
</style>