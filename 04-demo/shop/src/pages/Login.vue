<template>
    <div id="main">
      <LoginForm loginTitle="欢迎您来到乐记记账-请登录" action="http://localhost:8088/login"></LoginForm>
    </div>
</template>

<script>
import LoginForm from '../components/LoginForm'
export default {
  name: 'Login',
  components: {LoginForm}
}
</script>

<style scoped>

</style>
