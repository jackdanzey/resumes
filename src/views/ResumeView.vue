<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "RESUME! xxxxx",
      student: {},
      capstones: [],
      first_nameFilter: "",
      experience: {},
      education: {},
      skills: [],
    };
  },
  created: function () {
    axios.get("/students/" + this.$route.params.id + ".json").then((response) => {
      console.log(response.data);
      this.students = response.data;
    });
  },
  // methods: {
  //   filterName: function () {
  //     return this.students.filter((student) => {
  //       let lowerName = student.first_name.toLowerCase();
  //       let lowerNameFilter = this.nameFilter.toLowerCase();
  //       return lowerName.includes(lowerNameFilter);
  //     });
  //   },
  // },
};
</script>

<template>
  <div class="home">
    <!-- <div v-for="student in filterName()" v-bind:key="student.id">
      <h2>{{ student.first_name }}</h2>
      <p>{{ student.last_name }}</p>
      <router-link v-bind:to="`/students/${student.id}`">More details</router-link>
    </div> -->
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
