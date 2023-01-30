<template>



	
	<!-- Home -->

	<div class="home">
    <div class="home_slider_container">

      <!-- Home Slider -->
      <div class="owl-carousel owl-theme home_slider">

        <!-- Slider Item -->
        <div class="owl-item">
          <!-- Background image artist https://unsplash.com/@benwhitephotography -->
          <div class="home_slider_background" ></div>
          <div class="home_container">
            <div class="container">
              <div class="row">
                <div class="col">
                  <div class="home_content text-center">
                    <div class="home_logo"><img src="images/home_logo.png" alt=""></div>
                    <div class="home_text">
                      <div class="home_title">Complete Online Courses</div>
                    </div>
                    <div class="home_buttons">
                      <router-link to="courses"><div class="button home_button"><a>see all courses<div class="button_arrow"><i class="fa fa-angle-right" aria-hidden="true"></i></div></a></div></router-link>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Slider Item -->
        <div class="owl-item">
          <!-- Background image artist https://unsplash.com/@benwhitephotography -->
          <div class="home_slider_background" ></div>
          <div class="home_container">
            <div class="container">
              <div class="row">
                <div class="col">
                  <div class="home_content text-center">
                    <div class="home_logo"><img src="images/home_logo.png" alt=""></div>
                    <div class="home_text">
                      <div class="home_title">Come Learn with Us!</div>
                    </div>
                    <div class="home_buttons">
                      <router-link to="courses"><div class="button home_button">see all courses<div class="button_arrow"><i class="fa fa-angle-right" aria-hidden="true"></i></div></div></router-link>
                    </div>
                  </div>
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



export default {
    components: {

    },
   
    mounted() {

    },

}

</script>

<style scoped>
	@import "../../public/styles/main_styles.css";
	@import "../../public/styles/responsive.css";

  /*
  home_slider_container{
    background-image: url("images/index.jpg");
  }
  */


</style>