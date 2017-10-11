<template>
  <v-layout column>
    <v-flex xs6 offset-xs3 blue-grey--after>
      <div class="white elevation-2">
        <v-toolbar flat dense class="cyan">
          <v-toolbar-title>Login</v-toolbar-title>
        </v-toolbar>
  
        <div class="pl-4 pr-4 pt-2 pb-2 flat dense">
          <v-flex xs8 offset-xs2> 
            <v-text-field
              class="cyan--text text--lighten-2"
              type="email" 
              name="email"
              label="Email"
              v-model="email" />
            <br>
            <v-text-field
              class="cyan--text text--lighten-2"
              type="password" 
              name="password"
              v-model="password"
              label="Password" />
          </v-flex>
          <br>
          <div class="error" v-html="error" />
          <br>
          <v-btn
            class="cyan"
            @click="login">
            Login
          </v-btn>
        </div>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<style scoped>
.error {
  color: red;
}
</style>
