<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <RandomNum />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import RandomNum from '@/components/RandomNum.vue'

export default {
  name: 'HomeView',
  components: {
    RandomNum
  }
}
</script>
