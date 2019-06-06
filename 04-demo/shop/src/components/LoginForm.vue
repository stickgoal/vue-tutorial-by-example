<template>
    <div>
      <form v-bind:acion="actionUrl" @submit.prevent="doSubmit">
        <div class="item">
          <h2>{{loginTitleInner}}</h2>
        </div>
        <div class="item">
          <input type="text" v-model="username" placeholder="请输入用户名"/>
        </div>
        <div class="item">
         <input type="password" v-model="password" placeholder="请输入密码"/>
        </div>
        <div>
          <input type="submit" value="提交">
        </div>
      </form>
    </div>
</template>

<script>
import axios from 'axios'
import qs from 'qs'
import Message from 'element-ui/packages/Message'

export default {
  name: 'Login',
  props: ['action', 'loginTitle'],
  data () {
    return {
      username: '',
      password: '',
      actionUrl: this.action,
      loginTitleInner: this.loginTitle
    }
  },
  methods: {
    doSubmit (e) {
      const self = this

      // 注意坑点 axios post 传参需要用qs的stringify一下
      axios.post(self.actionUrl, qs.stringify({
        username: self.username,
        password: self.password
      })).then(response => {
        // response的结构是固定的，其中data表示返回的数据
        console.log(response)

        if (response.data.success) {
          self.$router.push({path: '/home'})
        } else {
          // element-ui提供的消息提示方式
          this.$message('校验失败')
        }
      })
    }
  }
}
</script>

<style scoped>
form .item{
  height: 3em;
  line-height: 2em;
}
  form{
    width: 400px;
    border:5px solid skyblue;
    margin:0 auto;
    border-radius: 10px;
  }
</style>
