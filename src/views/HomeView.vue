<template>
  <div class="home">
    {{ val }}
    <button @click="val = val + 1">+</button>
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
  },
  data() {
    return {
      val: 0,
    }
  },
}
</script>
