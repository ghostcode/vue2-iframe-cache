<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <AboutView v-show="isIframe"></AboutView>
    <div class="no-iframe" v-show="!isIframe">
      <transition>
        <keep-alive>
          <router-view></router-view>
        </keep-alive>
      </transition>
    </div>
  </div>
</template>

<script>
import AboutView from './views/AboutView.vue'
export default {
  name: 'App',
  components: {
    AboutView,
  },
  watch: {
    $route(to, from) {
      console.log(to, from)
      this.isIframe = to.fullPath === '/about'
      console.log('this.isIframe:', this.isIframe)
    },
  },
  data() {
    return {
      isIframe: false,
    }
  },
  beforeRouteEnter(to, from, next) {
    console.log('to, from, next:', to, from, next)
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
