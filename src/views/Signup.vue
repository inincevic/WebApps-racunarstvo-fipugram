<template>
  <div class="about">
    <h1>This is the sign up page</h1>
    <div class="container">
      <div class="row">
        <div class="col-sm"></div>
        <div class="col-sm">
          <form>
            <div class="form-group">
              <input
                type="email"
                v-model="username"
                class="form-control"
                id="exampleInputEmail1"
                aria-describedby="emailHelp"
                placeholder="Enter username"
              />
            </div>
            
            <br>

            <div class="form-group">
              <input
                type="password"
                v-model="password"
                class="form-control"
                id="exampleInputPassword1"
                placeholder="Password"
              />
            </div>

            <br>

            <div class="form-group">
              <input
                type="password"
                v-model="passwordConfirmation"
                class="form-control"
                id="exampleInputPassword2"
                placeholder="Confirm Password"
              />
            </div>
            <button type="button" @click="signup" class="btn btn-primary">Submit</button>
          </form>
        </div>
        <div class="col-sm"></div>
      </div>
    </div>
  </div>
</template>


<script>
import { initializeApp } from 'firebase/app';


export default {
  name: 'Signup',
  data() {
    return {
      username: '',
      password: '',
      passwordConfirmation: '',
    }
  },
  methods: {
    signup() {
      if(this.password == this.passwordConfirmation) {
        initializeApp
        .auth()
        .createUserWithEmailAndPassword(this.username, this.password)
        .then(function() {
          console.log("Registration successful");
        })
        .catch(function(error) {
          console.error("Doslo je do greske", error)
        })
      }
      else altert("Passwords do not match");
    }
  }
}
</script>
