<template>

  <div class="jobs">
        <h2>Jobs</h2>
      <div class="job" v-for="job in jobs" :key="job.id"><h3>{{job.title}}</h3></div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            jobs:[{id:1,title:'webdesigner',details:'lorem'},{id:2,title:'UX Designer',details:'lorem'},{id:3,title:'Vue Developer',details:'lorem'},]
        }
    }
}
</script>

<style>

</style>