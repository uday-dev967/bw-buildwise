<template>
  <v-container class="login-page">
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="4">
        <v-card elevation="6" light>
          <v-card-title class="headline">Login</v-card-title>
          <v-card-text>
            <v-form @submit.prevent="login">
              <v-text-field
                v-model="email"
                label="Email"
                outlined
                required
                type="email"
              ></v-text-field>

              <v-text-field
                v-model="password"
                label="Password"
                outlined
                required
                :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                :type="showPassword ? 'text' : 'password'"
                @click:append="showPassword = !showPassword"
              ></v-text-field>

              <v-btn type="submit" color="primary" block> Login </v-btn>
            </v-form>
          </v-card-text>
        </v-card>
      </v-col>
      <img
        src="../static/loginback.png"
        alt="loginback"
        class="login-page-image"
      />
    </v-row>
  </v-container>
</template>

<script>
// import loginBack from '~/static/loginback.png'
export default {
  name: 'Login',
  data() {
    return {
      email: '',
      password: '',
      showPassword: false,
    }
  },
  methods: {
    login() {
      // Implement your login logic here
      // eslint-disable-next-line no-console
      console.log('Login with:', this.email, this.password)
    },
  },
}
</script>

<style lang="scss" scoped>
.login-page {
  height: 100vh;
  width: 100vw;
  background-color: #f7f7f9;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  &-image {
    position: absolute;
    bottom: 0;
    left: 0;
    z-index: 0;
  }
}
</style>
