<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "RESUME! xxxxx",
      students: {},
      capstones: [],
      nameFilter: {},
      experiences: [],
      educations: [],
      skills: [],
    };
  },
  created: function () {
    axios.get("/students/1.json").then((response) => {
      console.log(response.data);
      this.students = response.data;
      this.capstones = response.data.capstones;
      this.experience = response.data.experiences;
      this.educations = response.data.educations;
      this.skills = response.data.skills;
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
    <ul>
      <li>
        <h2>Education</h2>
        <div v-for="education in educations" v-bind:key="education.id">{{ education.university_name }}</div>
      </li>
      <li><h2>Experience</h2></li>
      <!-- <div v-for="(value, key) in experience" v-bind:key="(key, value)">{{ key }}: {{ value }}</div> -->
      <li><h2>Skills</h2></li>
      <div v-for="skill in skills" v-bind:key="skill.id">{{ skills.skill_name }}</div>
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
