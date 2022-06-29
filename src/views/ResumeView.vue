<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "RESUME! xxxxx",
      student: {
        first_name: "Jack",
        last_name: "Danzey",
        email: "jack@test.com",
        phone_number: "2225551111",
        short_bio: "Actualize student in AlleyOOP cohort, currently on week 10 of 12!",
        linkedIn_url: "www.linkedin.com/jack",
        twitter: "@jackdanzey",
        personal_blog_url: "www.jack.com",
        resume: "resume.url",
        github_url: "github.com/jackdanzey",
        photo: "https://i.pinimg.com/564x/1b/14/34/1b1434c7d78bca9e24bcb89e5126903c.jpg",
      },
      capstone: {
        name: "Super cool fun app",
        description: "Way cool app that is fun and everything",
        url: "www.coolapp.com",
        screenshot: "cool.jpg",
      },
      nameFilter: "",
      experience: {
        start_date: "Today",
        end_date: "N/A",
        job_title: "Smart Guy",
        company_name: "Syntech",
        details: "",
      },
      education: {
        start_date: "2010",
        end_date: "2011",
        degree: "Yes",
        university: "Steve Harvard",
        details: "",
      },
    };
  },
  created: function () {
    axios.get("/students/" + this.$route.params.id + ".json").then((response) => {
      console.log(response.data);
      this.students = response.data;
    });
  },
  methods: {
    // filterName: function () {
    // return this.students.filter((student) => {
    // let lowerName = student.first_name.toLowerCase();
    // let lowerNameFilter = this.nameFilter.toLowerCase();
    // return lowerName.includes(lowerNameFilter);
    // });
    // },
  },
};
</script>

<template>
  <div class="home">
    <!-- <div v-for="student in filterName()" v-bind:key="student.id"> -->
    <!-- <h2>{{ student.first_name }}</h2> -->
    <!-- <p>{{ student.last_name }}</p> -->
    <!-- <router-link v-bind:to="`/students/${student.id}`">More details</router-link> -->
    <!-- </div> -->
    <div class="shadow-lg p-3 mb-5 bg-body rounded">
      <div class="mx-auto" style="width: 1000px">
        <img v-bind:src="student.photo" v-bind:alt="student.first_name" class="image-fit" />
        <h1>{{ student.first_name }} {{ student.last_name }}</h1>
        <h3>Email: {{ student.email }} | Phone Number:{{ student.phone_number }} |</h3>
        <h5>
          <a :href="`${student.linkedIn_url}`">{{ student.linkedIn_url }}</a>
          | Twitter: {{ student.twitter }} |
          <a :href="`${student.personal_blog_url}`">{{ student.personal_blog_url }}</a>
          |
          <a :href="`${student.resume}`">{{ student.resume }}</a>
          |
          <a :href="`${student.github_url}`">{{ student.github_url }}</a>
          |
        </h5>
        <h3>{{ student.short_bio }}</h3>
      </div>
    </div>
    <ul>
      <li v-for="(value, key) in experience" v-bind:key="(key, value)">
        <h2>{{ key }}:</h2>
        {{ value }}
      </li>
      <li v-for="(value, key) in education" v-bind:key="(key, value)">
        <h2>{{ key }}:</h2>
        {{ value }}
      </li>
    </ul>
    <div>
      <h3>{{ capstone.name }}</h3>
      <p>{{ capstone.description }}</p>
      <p>{{ capstone.url }}</p>
      <p>{{ capstone.screenshot }}</p>
    </div>
    <a class="twitter-timeline" href="https://twitter.com/PhilosophyDose_?ref_src=twsrc%5Etfw">
      Tweets by PhilosophyDose_
    </a>
  </div>
</template>

<style>
.image-fit {
  height: 25%;
  width: 25%;
  object-fit: cover;
}
</style>
