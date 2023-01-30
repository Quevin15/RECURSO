 <template>
	<!-- Header -->

	<header class="header">
			
		<!-- Top Bar -->
		<div class="top_bar">
			<div class="top_bar_container">
				<div class="container">
					<div class="row">
						<div class="col">
							<div class="top_bar_content d-flex flex-row align-items-center justify-content-start">
								<ul class="top_bar_contact_list">
									<li><div class="question">Have any questions?</div></li>
									<li>
										<div>(009) 35475 6688933 32</div>
									</li>
									<li>
										<div>info@elaerntemplate.com</div>
									</li>
								</ul>
							</div>
						</div>
					</div>
				</div>
			</div>				
		</div>

		<!-- Header Content -->
		<div class="header_container">
			<div class="container">
				<div class="row">
					<div class="col">
						<div class="header_content d-flex flex-row align-items-center justify-content-start">
							<div class="logo_container">
								<router-link to="/">
									<div class="logo_content d-flex flex-row align-items-end justify-content-start">
										<div class="logo_img"><img :src="require(`/public/images/logo.png`)" alt=""/></div>
										<div class="logo_text">learn</div>
									</div>
								</router-link>
							</div>
							<nav class="main_nav_container ml-auto">
								<ul class="main_nav">
                  <li ><router-link to="/"><a>home</a></router-link></li>
									<li><router-link to="courses"><a>courses</a></router-link></li>
                  <li v-if ="!userLoggedIn()"><router-link to="register"><a>Register</a></router-link></li>
                  <li v-if ="userLoggedIn()"><router-link to="myCourses"><a>My courses</a></router-link></li>
                  <li v-if ="!userLoggedIn()"><router-link to="login"><a>Login</a></router-link></li>
                  <li v-if ="userLoggedIn()"><button @click="userLogout()"><a>Logout</a></button></li>
									<li v-if ="userLoggedIn()">Welcome {{user.name}}!</li>
                  <li v-if ="!userLoggedIn()">Welcome STRANGER!</li>
								</ul>
							</nav>

						</div>
					</div>
				</div>
			</div>
		</div>
	</header>
</template>

<script>


export default {
  data(){
    return{
      user: {}
    }
  },
  methods: {
    userLoggedIn(){
      for(let i in this.user) return true
      return false
    },
    userLogout(){
      this.$store.commit('user/logoutUser')
      this.userLoggedIn();
    },

  },
  mounted(){
    this.user = this.$store.getters['user/getUser']
  }
}


</script>  
