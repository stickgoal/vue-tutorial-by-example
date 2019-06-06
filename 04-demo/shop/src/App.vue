<template>
  <div id="app">
    <header>
      <router-link to="/home">记账</router-link>
      <router-link to="/login">登录</router-link>
      <router-link to="/stat">统计</router-link>
    </header>
    <router-view></router-view>
  </div>
</template>

<script>
import Login from './pages/Login'
export default {
  name: 'App',
  components: {Login}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
