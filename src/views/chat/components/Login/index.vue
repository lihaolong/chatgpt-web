<script lang="ts">
import axios from 'axios'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'LoginForm',
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    async login() {
      // TODO: implement login functionality
      try {
        const response = await axios.post('/api/login', {
          email: this.email,
          password: this.password,
        })
        localStorage.setItem('token', response.data.token)
        this.$router.push('/')
      }
      catch (error) {
        console.error(error)
      }
    },
  },
})
</script>

<template>
  <form class="form">
    <div class="form__group">
      <label for="email" class="form__label">Email:</label>
      <input id="email" v-model="email" type="email" class="form__input">
    </div>
    <div class="form__group">
      <label for="password" class="form__label">Password:</label>
      <input id="password" v-model="password" type="password" class="form__input">
    </div>
    <button type="submit" class="button" @click.prevent="login">
      Login
    </button>
  </form>
</template>

<style lang="less">
@import url(./style.less);
</style>
