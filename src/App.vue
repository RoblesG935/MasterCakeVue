<template>
  <div id="app">
    <b-container>
      <b-row>
        <b-col></b-col>
        <b-col cols="6">
          <b-card title="Login">
          <b-form @submit="login">


            <b-form-group label="Username">
              <b-form-input v-model="username" placeholder="Enter your username" required></b-form-input>
            </b-form-group>

            <b-form-group label="Password">
              <b-form-input v-model="pass" type="password" placeholder="Enter your password" required></b-form-input>
            </b-form-group>

            <b-button type="submit" variant="primary">Login</b-button>
          </b-form>
        </b-card>

        </b-col>
        <b-col></b-col>
        {{ username }}
        {{ pass }}
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios';


export default {
  name: 'App',
  components: {

  },
  data() {
    return {
      username: "",
      pass: ""
    }
  },
  methods: {
     async login() {
      const requestBody={
        usrn: this.username,
        password: this.pass

      }
     const serverUrl = "https://kind-lime-meerkat-gear.cyclic.app/users/login";
     const response = await axios.post(
      `${serverUrl}users/login`,
      requestBody
      
     );
     console.log(response);
     


    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

