<template>
  <div class="users-signup register-page full-screen">
    <div class="wrapper">
      <div class="page-header" style="background-image: url('../assets/img/sections/soroush-karimi.jpg');">
        <div class="filter"></div>
        <div class="container">
          <div class="row">
            <div class="col-lg-6 col-md-6 col-sm-7 col-12 ml-auto">
              <div class="info info-horizontal">
                <div class="icon">
                  <i class="fa fa-umbrella"></i>
                </div>
                <div class="description">
                  <h3> We've got you covered </h3>
                  <p>Larger, yet dramatically thinner. More powerful, but remarkably power efficient. Everything you need in a single case.</p>
                </div>
              </div>
              <div class="info info-horizontal">
                <div class="icon">
                  <i class="fa fa-map-signs"></i>
                </div>
                <div class="description">
                  <h3> Clear Directions </h3>
                  <p>Efficiently unleash cross-media information without cross-media value. Quickly maximize timely deliverables for real-time schemas.</p>
                </div>
              </div>
              <div class="info info-horizontal">
                <div class="icon">
                  <i class="fa fa-user-secret"></i>
                </div>
                <div class="description">
                  <h3> We value your privacy </h3>
                  <p>Completely synergize resource taxing relationships via premier niche markets.</p>
                </div>
              </div>
            </div>
            <div class="col-lg-6 col-md-6 col-sm-5 col-12 mr-auto">
              <div class="card card-register">
                <h3 class="card-title text-center">Register</h3>
                <div class="social">
                  <button href="#paper-kit" class="btn btn-just-icon btn-facebook"><i class="fa fa-facebook"></i></button>
                  <button href="#paper-kit" class="btn btn-just-icon btn-google"><i class="fa fa-google"></i></button>
                  <button href="#paper-kit" class="btn btn-just-icon btn-twitter"><i class="fa fa-twitter"></i></button>
                </div>
                <div class="division">
                  <div class="line l"></div>
                  <span>or</span>
                  <div class="line r"></div>
                </div>
                <form class="register-form" v-on:submit.prevent="submit()">
                  <input type="text" class="form-control" placeholder="Email" v-model="email">
                  <input type="password" class="form-control" placeholder="Password" v-model="password">
                  <input type="password" class="form-control" placeholder="Confirm Password" v-model="passwordConfirmation">
                  <button type="submit" class="btn btn-block btn-round">Register</button>
                </form>
                <div class="login">
                  <p>Already have an account?
                    <a href="/userslogin">Log in</a>.</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import UserService from '../../services/UserService.js';
export default {
  data: function() {
    return {
      name: "",
      email: "",
      password: "",
      passwordConfirmation: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        name: this.name,
        email: this.email,
        password: this.password,
        password_confirmation: this.passwordConfirmation
      };
      UserService.postUser(params)
        .then(response => {
          this.$router.push("/userslogin");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>