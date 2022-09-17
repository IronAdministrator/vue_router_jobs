<template>
  <div v-if="job">
    <h1>{{job.title}}</h1>
    <p>The Job ID is: {{ job.id }}</p>
    <p>job.details</p>
  </div>
  <div v-else>
    <p>Loading...</p>
  </div>
</template>

<script>
export default {
  props: ['id'],
  // data() {
  //   return {
  //     id: this.$route.params.id
  //   }
  // },
  data() {
    return {
      job: null
    }
  },
  mounted () {
    fetch('http://localhost:3000/jobs/' + this.id)
    .then((res) => { return res.json()})
    .then((data) => { return this.job = data})
    .catch((err) => console.log(err.message))
  },
}
</script>

<style>

</style>