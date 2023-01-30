<template>
<div>


  
<Header />



   	<!-- Courses -->

	<div class="courses">
		<div class="container">



			<div class="row courses_row">
			

				<div class="col-lg-10 offset-lg-1">
					<div class="section_title text-center"><h2>Choose your new course!</h2></div>
					<br>
				</div>

				<!-- Course -->


        <div v-for="course in courses" :key="course.id">
        <div class="col-lg-4 col-md-6">
          <div class="course">
<!--
            <div class="course_image"><img src="require(`/public/images/${$course.image}`)" alt=""></div>
-->
            <div class="course_body">
              <div class="course_header d-flex flex-row align-items-center justify-content-start">
                <div class="course_tag"><a href="#">{{course.cat_name}}</a></div>
                <div class="course_price ml-auto">Price: <span>{{course.price}}</span></div>
              </div>
              <div class="course_title"><h3><a href="#">{{course.name}}</a></h3></div>
              <div class="course_text">{{course.description}}</div>
              <div class="course_footer d-flex align-items-center justify-content-start">
<!--
                <div class="course_author_image"><img :src="require(`public/images/${course.teacher_image}`)" ></div>
-->
                <div class="course_author_name">By <a href="#">James S. Morrison</a></div>
                <div class="course_sales ml-auto"><span>352</span> Sales</div>
              </div>
              <br><div class="text-center"><div class="button"><a href="#">Enroll</a></div></div>
            </div>
          </div>
        </div>
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

    components: {
        Footer,
        Header
    },
  

    data() {
        return {
        courses: [],
        }
    },
    mounted() {
     this.getCourses();
   },

  methods: {
    async getCourses() {
      if (await this.$store.dispatch('courses/getCoursesFromDB')) {
        this.courses = this.$store.getters['courses/getCourses']
      }
    },
    computed: {},
  }
}

</script>

<style scoped>

</style>