<template>
    <div class="main-container align-center justify-center" style="height:100vh">
      <v-card max-width="800" class="mx-auto" outlined>
          <v-layout column align-center>
    
            <div class="logo-container"><img src="../assets/company.png" alt="Logo" class="logo-img"></div>

            <div class="social-link-button-container">
          <v-row class="mx-12 mt-5">
            <v-col cols="auto" class="mr-auto">
              <v-btn outlined color="blue-grey"><v-icon color="red left">mdi-google</v-icon>Google </v-btn>
            </v-col>
  
            <v-col cols="auto">
              <v-btn outlined color="blue-grey"><v-icon color="blue" left>mdi-facebook</v-icon>Facebook</v-btn>
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
            <v-text-field outlined v-model="name" :rules="nameRules" label="Name" prepend-inner-icon="mdi-account-circle" required></v-text-field>
          <v-text-field outlined v-model="email" :rules="emailRules" label="E-mail" prepend-inner-icon="mdi-email" required></v-text-field>
          <v-text-field outlined v-model="password" :rules="passwordRules" label="Password" type="password" prepend-inner-icon="mdi-lock" required></v-text-field>
          <v-text-field outlined v-model="confirmpass" :rules="confirmpassRules" label="Confirm Password" type="password" prepend-inner-icon="mdi-lock" required></v-text-field>
          <v-row align="center" justify="center">
          <v-btn @click="signIn" color="success" class="mr-4" block>Sign in</v-btn>
        </v-row>
       </v-form>
        </v-layout>
  
      </v-card>
    </div>
  </template>
  
  <script>
  export default {
    layout: "auth",
    name: "signup",
    data() {
      return {
        name:'',
        email: '',
        password: '',
        confirmpass: '',
        nameRules: [
          v => !!v || 'Name is required',
          v => (v && v.length <= 50) || 'Name is Required',
        ],
        emailRules: [
          v => !!v || 'Email is required',
          v => /.+@.+\..+/.test(v) || 'Email must be valid',
        ],
        passwordRules: [
          v => !!v || 'Password is required',
          v => (v && v.length >= 6) || 'Password must be at least 6 characters',
        ],
        confirmpassRules: [
          v => !!v || 'Confirmation Password is required',
          v => v === this.password || 'Password must match'
        //   v => (v && v.length >= 6) || 'Password must be at least 6 characters',
        ],
      };
    },
    methods: {
      signIn() {
        if(this.$refs.form.validate()){
          console.log("Succesfully LogIn");
          this.$router.push("/")
        }
      },

    },
  };
  </script>
  
  <style scoped>
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