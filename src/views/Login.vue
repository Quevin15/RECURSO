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
              <form @submit.prevent="handleSubmit()" id="contact_form" class="contact_form">
                <div>
                  <div class="row">
                    <div class="col-lg-12  contact_name_col">
                      <label for="email">Email:</label>
                      <input type="email" class="contact_input" required="required" v-model="user.email">
                    </div>
                  </div>
                </div>
                <div class="row">
                  <div class="col-lg-12 contact_name_col">
                    <label for="passwd1">Password:</label>
                    <input type="password" class="contact_input" required="required" v-model="user.password">
                  </div>
                </div>
                <input style="float:right" type="submit" class="contact_button" value="Login">
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
    name: 'login',
    components: {
        Footer,
        Header
    },

  data() {
    return {
      user: {
        id: '',
        name: '',
        email: '',
        session_id: '',
      },
      message:''
    }
  },

  methods: {
    handleSubmit: function () {
      this.loginUser(this.user)
    },

    async loginUser(user) {
      if (await this.$store.dispatch('user/loginUser', user)) {
        this.userLoggedIn = true;
        localStorage.setItem('message',"Welcome back " + this.$store.getters['user/getUser'].name + " !")
        await this.$router.push('/message')
      } else {
        this.message = "Wrong password or email";
        this.user.password=""
      }
    },

    clear() {
      this.user = {}
    },
  },

  computed: {},
}
</script>
<style scoped>
</style>