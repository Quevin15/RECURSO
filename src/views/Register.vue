<template>
    <div>
        <Header />
            <!-- Contact -->
      <div class="contact">
        <div class="container-fluid">
          <div class="row row-xl-eq-height">
            <div class="col-xl-3">
            </div>
            <!-- Contact Content -->
            <div class="col-xl-6">
              <div class="contact_content">
                <div class="contact_form_container">
                  <form @submit.prevent="handleSubmit" id="contact_form" class="contact_form">
                    <div>
                      <div class="row">
                        <div class="col-lg-6 contact_name_col">
                          <label for="name">Name:</label>
                          <input type="text" class="contact_input" required="required" v-model="user.name">
                        </div>
                        <div class="col-lg-6">
                          <label for="email">Email:</label>
                          <input type="email" class="contact_input" required="required" v-model="user.email">
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-lg-6 contact_name_col">
                        <label for="passwd1">Password:</label>
                        <input type="password" class="contact_input" required="required" v-model="user.password">
                      </div>
                      <div class="col-lg-6">
                        <label for="passwd2">Repeat Password:</label>
                        <input type="password" class="contact_input" required="required" v-model="passwordConfirmation">
                      </div>
                    </div>
                    <input style="float:right" type="submit" class="contact_button" value="Register">
                    <button type="button" v-if="this.message !== ''" class="btn btn-danger">{{message}}</button>
                  </form>
                </div>
              </div>
            </div>
            <div class="col-xl-3">
            </div>

          </div>

        </div>
      </div>





        <Footer />
    </div>
</template>
<script>
import Footer from '@/components/Footer.vue'
import Header from '@/components/Header.vue'

export default {
    name: 'register',
    components: {
        Footer,
        Header
    },
  data() {
    return {
      user: {
        name: '',
        email: '',
        password: '',
      },
      passwordConfirmation: '',
      message: ''
    }
  },

  methods: {
    handleSubmit: function(){
      if(this.invalidEmail) {
        this.message = "Invalid email";
        this.user.email ='';
        return;
      }
      else if(this.invalidPassword){
        this.message="password too short"
        this.user.pasword ='';
        return;
      }
      else if(this.invalidRepeatPassword) {
        this.message = "password are different"
        this.passwordConfirmation = '';
        return;
      }
      else if(this.invalidName){
        this.message = "The name must not be blank"
        return;
      }
      this.addUser(this.user);
    },

    async addUser(user) {
      if (await this.$store.dispatch('user/userExists', user)) {
        this.message ="User already exists";
      }
      else if (await this.$store.dispatch('user/addUser')) {
        this.message = '';
        localStorage.setItem('message','Welcome! You can now login')
        await this.$router.push('/message')
      } else {
        this.message="There was an error during registration"
      }
    },
    erase() {
      this.user = {};
    },
  },

  computed: {
    invalidName: function(){
      return this.user.name === '';
    },

    invalidPassword: function () {
      return this.user.password === '' || this.user.password.length < 8;
    },

    invalidRepeatPassword: function () {
      return this.user.password !== this.passwordConfirmation;
    },

    invalidEmail: function () {
      const regExpr = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
      return !this.user.email.match(regExpr);
    },
  },
}

</script>

<style scoped>
</style>