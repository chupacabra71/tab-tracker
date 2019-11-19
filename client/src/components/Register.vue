<template>
  <v-app>
    <v-layout column>
      <v-flex xs6 offset-xs3>
        <v-card>
          <div class="elevation-2">
            <v-toolbar app flat dense class="orange" dark>
              <v-toolbar-title>Register</v-toolbar-title>
            </v-toolbar>2
            <div class="pl-4 pr-4 pt-2 pb-2">
              <input
                type="email"
                name="email"
                v-model="email"
                placeholder="email" />
              <br>
              <input
                type="password"
                name="password"
                v-model="password"
                placeholder="password" />
              <div class="error" v-html="error" />
              <br>
                <v-btn
                class="cyan"
                @click="register">
                  Register
                </v-btn>
            </div>
          </div>
        </v-card>
      </v-flex>
    </v-layout>
  </v-app>
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
    async register () {
      try {
        console.log('CLIENT: register button clicked', this.email, this.password)
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  color: red;
}
</style>
