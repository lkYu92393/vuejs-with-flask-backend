<template>
  <div id="home">
    <div>
      AI Training
    </div>
    <div>
      Current progress: {{ progress }}
    </div>
    <div></div>
    <div v-if="hasAPI">
      <button @click="startGrading">Start</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      progress: 'x/y'
      ,hasAPI: false
    }
  },
  methods: {
    getProgress () {
      const path = `/api/progress`
      axios.get(path)
        .then(response => {
          this.progress = response.data.progress
          this.hasAPI = true
        })
        .catch(error => {
          console.log(error)
        })
    },
    startGrading () {
      this.$router.push({ path: '/grading' })
    }
  },
  created () {
    this.getProgress()
  }
}
</script>

<style>
#home {
  display: grid;
  grid-template-rows: 1fr 1fr 1fr;
  grid-template-columns: 1fr;
  row-gap: 10px;
}
</style>
