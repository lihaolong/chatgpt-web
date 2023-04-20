<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'
import { ElButton, ElForm, ElFormItem, ElInput } from 'element-plus'

const email = ref('')
const password = ref('')

async function login() {
  try {
    const response = await axios.post('/api/login', {
      email: email.value,
      password: password.value,
    })
  } catch (error) {
  }
}
</script>

<template>
  <ElForm label-position="top">
    <ElFormItem label="Email">
      <ElInput v-model="email" type="email" />
    </ElFormItem>
    <ElFormItem label="Password">
      <ElInput v-model="password" type="password" />
    </ElFormItem>
    <ElFormItem>
      <ElButton type="primary" @click.prevent="login">
        Login
      </ElButton>
    </ElFormItem>
  </ElForm>
</template>

<style lang="less">
@import url(./style.less);
</style>
