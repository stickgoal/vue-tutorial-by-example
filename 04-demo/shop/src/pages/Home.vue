<template>
  <el-container>
    <el-main>
      <el-row>
        <el-col :span="8" :offset="8">
          <h2>来记账吧</h2>

          <el-form :rules="rules" @submit.prevent="onSubmit" :mnpodel="form" ref="keepForm">
            <el-form-item>
              <el-switch @change="changeDirection"
                         v-model="form.direction"
                         active-text="支出"
                         inactive-text="收入"
                         active-color="#ff4949"
                         inactive-color="#13ce66"
              >
              </el-switch>
            </el-form-item>
            <el-form-item label="分类">
              <el-form-item>
                <el-radio-group v-model="form.category" size="small" prop="category">
                  <el-radio-button border v-for=" tag in currentTags" :key="tag" :label="tag">{{tag}}</el-radio-button>
                </el-radio-group>
              </el-form-item>
            </el-form-item>
            <el-form-item label="金额">
              <el-col :span="12" :offset="4" class="block">
                <el-slider
                  v-model="form.amount"
                  show-input>
                </el-slider>
              </el-col>
            </el-form-item>
            <el-form-item label="备注" prop="memo">
              <el-input type="textarea" :autosize="{ minRows: 2, maxRows: 4}" v-model="form.memo" clearable></el-input>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit('keepForm')">记一笔</el-button>
              <el-button type="reset">重置</el-button>
            </el-form-item>
          </el-form>
        </el-col>
      </el-row>
    </el-main>
  </el-container>
</template>

<script>

import axios from 'axios'
import qs from 'qs'

export default {
  name: 'Home',
  data () {
    return {
      form: {
        direction: true,
        amount: 0,
        category: '',
        memo: ''
      },
      paymentTags: [],
      gainTags: [],
      currentTags: [],
      rules: {
        category: [{required: true, message: '选择分类', trigger: 'blur'}],
        memo: [{required: true, message: '请填写备注', trigger: 'blur'},
          {min: 3, max: 2048, message: '字符不符合要求', trigger: 'blur'}
        ]
      }
    }
  },
  methods: {
    onSubmit (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          axios.post('http://localhost:8088/keep', qs.stringify(this.form)).then(res => {
            if (res.data.success) {
              this.$notify('记账成功啦')
            } else {
              this.$notify(res.data.message)
            }
          }).catch(function (err) {
            console.error(err)
          })
          return true
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    changeDirection () {
      if (this.form.direction) {
        this.currentTags = this.paymentTags
      } else {
        this.currentTags = this.gainTags
      }
      this.form.category = this.currentTags[0]
    }
  },
  mounted () {
    // 从后台获取标签
    axios.get('http://localhost:8088/getTags').then(response => {
      if (response.data.success) {
        this.paymentTags = response.data.paymentTags
        this.gainTags = response.data.gainTags
        this.currentTags = this.paymentTags
        this.form.category = this.currentTags[0]
      }
    })
  }
}
</script>

<style scoped>

</style>
