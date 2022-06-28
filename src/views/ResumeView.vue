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
    };
  },
  created: function () {
    axios.get("/students/" + this.$route.params.id + ".json").then((response) => {
      console.log(response.data);
      this.students = response.data;
    });
  },
  methods: {},
};
</script>

<template>
  <div class="home">
    <div class="container">
      <img v-bind:src="student.photo" v-bind:alt="student.first_name" class="image-fit" />
      <h1>{{ student.first_name }} {{ student.last_name }}</h1>
      <h2>Contact Information: {{ student.email }} | {{ student.phone_number }} |</h2>
      <h3>
        <a :href="`${student.linkedIn_url}`">{{ student.linkedIn_url }}</a>
        | Twitter: {{ student.twitter }} |
        <a :href="`${student.personal_blog_url}`">{{ student.personal_blog_url }}</a>
        |
        <a :href="`${student.resume}`">{{ student.resume }}</a>
        |
        <a :href="`${student.github_url}`">{{ student.github_url }}</a>
        |
      </h3>
      <h2>{{ student.short_bio }}</h2>
    </div>
  </div>
</template>

<style>
.image-fit {
  height: 25%;
  width: 25%;
  object-fit: cover;
}
</style>
