<template>
  <div class="main-container align-center justify-center" style="height:100vh">
    <v-card max-width="800" class="mx-auto" outlined>
        <v-layout column align-center>
          <!-- Your logo here -->
          <div class="logo-container"><img src="../assets/company.png" alt="Logo" class="logo-img"></div>

          <div class="social-link-button-container">
            <v-row class="mx-12 mt -5">
            <v-col cols="auto" class="mr-auto">
              <v-btn outlined color="blue-grey"><v-icon color="red" left>mdi-google</v-icon>GOOGLE</v-btn>
            </v-col>
            <v-col cols="auto">
              <v-btn outlined color="blue-grey"><v-icon color="blue" left>mdi-facebook</v-icon>FACEBOOK</v-btn>
            </v-col>
          </v-row>
        </div>

        <v-row justify="center">
          <v-col cols="auto">
            <div class="mb-2">----------Or Sign In With----------</div>
          </v-col>

        </v-row>

       <!-- <v-form ref="form" v-model="valid" lazy-validation class="mx-15"> -->
        <v-form ref="form" v-model="valid" lazy-validation class="px-3 py-8">
        <v-text-field outlined="15" v-model="email" :rules="emailRules" label="E-mail" prepend-inner-icon="mdi-email" required></v-text-field>
        <v-text-field outlined="15" v-model="password" :rules="passwordRules" label="Password" type="password" prepend-inner-icon="mdi-lock" required></v-text-field>
        <v-row align="center" justify="center">
          <v-btn :disabled="!valid" color="success" class="mr-4" @click="validate" block>
              SIGNIN
            </v-btn>

      </v-row>
      <v-row align="center" justify="center">
        <v-btn text color="blue" @click="goToSignUp" class="mt-2">Create an Account</v-btn></v-row>
     </v-form>
      </v-layout>

    </v-card>
  </div>
</template>

<script>
export default {
  layout: "auth",
  name: "IndexPage",
  data() {
    return {
      valid: true,
      email: '',
      password: '',
      emailRules: [
        v => !!v || 'Email is required',
        v => /.+@.+\..+/.test(v) || 'Email must be valid',
      ],
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 6) || 'Password must be at least 6 characters',
      ],
    };
  },
  computed: {
    isFormFilled() {
      return this.username && this.password;
    },
  },
  methods: {
    validate() {
      if(this.$refs.form.validate()){
        console.log("Succesfully LogIn");
        this.$router.push("/dashboard")
      }
    },
    goToSignUp() {
      // Navigate to sign-up page
      this.$router.push('/signup');
    },
  },
};
</script>

<style scoped>

.main-container{
  display: flex;
  align-items: center;
  flex-direction: column;
  height: 100%;
  width: 100%;
  /* background-image: url(); */
  background-size: cover;
  background-position: center;
  height: 100vh;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.card {
  width: 400px;
}

.logo {
  text-align: center;
  margin-bottom: 20px;
}

.social-buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.or-text {
  margin: 0 15px;
}

.signin-btn {
  margin-top: 20px;
}

.create-account-btn {
  margin-top: 10px;
}
</style>