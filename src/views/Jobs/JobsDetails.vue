<template>
<div class="job">
  <h2>Job Destails</h2>
  <div class="details" v-if="job">
<p>{{job.title}}</p>
<p>{{job.details}}</p>
  </div>
  <div v-else>
    <p>Loading...</p>
  </div>
  </div>
  <div class="back">
    <button class="btn-back" @click="goBack">Back</button>
  </div>
</template>

<script>
export default {
    props:['id'],
    data(){
      return{
        job:null
      }
    },
    async created(){
      this.job = await this.fetchJob()  
    },
    methods:{
      async fetchJob(){
        const res = await fetch(`/api/jobs/${this.$props.id}`)
        const job = await res.json()
        return job
      },
      goBack(){
        this.$router.go(-1)
      }
    }
}
</script>

<style>

</style>