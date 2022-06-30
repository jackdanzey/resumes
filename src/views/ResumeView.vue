<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "RESUME! xxxxx",
      student: {},
      capstones: [],
      first_nameFilter: "",
      experiences: [],
      educations: [],
      skills: [],
    };
  },
  created: function () {
    axios.get("/students/1.json").then((response) => {
      this.student = response.data;
      this.capstones = response.data.capstones;
      this.experiences = response.data.experiences;
      this.educations = response.data.educations;
      this.skills = response.data.skills;
      console.log(response.data);
    });
  },
  methods: {
    // filterName: function () {
    // return this.students.filter((student) => {
    // let lowerName = student.first_name.toLowerCase();
    // let lowerNameFilter = this.first_nameFilter.toLowerCase();
    // return lowerName.includes(lowerNameFilter);
    // });
    // },
  },
};
</script>

<template>
  <div class="home">
    <!-- <p> -->
    <!-- Search by Name: -->
    <!-- <input type="text" v-model="first_nameFilter" list="first_name" /> -->
    <!-- <datalist id="first_name"> -->
    <!-- <option v-for="student in students" v-bind:key="student.id">{{ student.first_name }}</option> -->
    <!-- </datalist> -->
    <!-- </p> -->
    <!-- <div v-for="student in filterName()" v-bind:key="student.id"> -->
    <!-- <h2>{{ student.first_name }}</h2> -->
    <!-- <p>{{ student.last_name }}</p> -->
    <!-- <router-link v-bind:to="`/students/${student.id}`">More details</router-link> -->
    <!-- </div> -->
    <span class="border border-bottom-0">
      <div class="shadow-lg p-3 mb-5 bg-body rounded">
        <div class="mx-auto" style="width: 900px">
          <img v-bind:src="student.photo" v-bind:alt="student.first_name" class="image-fit" />
          <h1>{{ student.first_name }} {{ student.last_name }}</h1>
          <h3>Email: {{ student.email }} | Phone Number: {{ student.phone_number }} |</h3>
          <h5>
            <a :href="`${student.linkedin}`">{{ student.linkedin }}</a>
            | Twitter: {{ student.twitter_handle }} |
            <a :href="`${student.personal_website}`">{{ student.personal_website }}</a>
            |
            <a :href="`${student.online_resume}`">{{ student.online_resume }}</a>
            |
            <a :href="`${student.github}`">{{ student.github }}</a>
          </h5>
          <h3>{{ student.short_bio }}</h3>
        </div>
      </div>
    </span>
    <span class="border border-bottom-0">
      <div class="shadow-lg p-3 mb-5 bg-body rounded">
        <div class="mx-auto" style="width: 900px">
          <h2>Education</h2>
          <div v-for="(value, key) in experiences" v-bind:key="(key, value)">{{ key }}: {{ value }}</div>
        </div>
      </div>
    </span>
    <span class="border border-bottom-0">
      <div class="shadow-lg p-3 mb-5 bg-body rounded">
        <div class="mx-auto" style="width: 900px">
          <h2>Experience</h2>
          <!-- <div v-for="(value, key) in education" v-bind:key="(key, value)">{{ key }}: {{ value }}</div> -->
          <div v-for="experience in experiences" v-bind:key="experience.id">
            <p>Title: {{ experience.job_title }}</p>
            <p>Company: {{ experience.company_name }}</p>
            <p>Details: {{ experience.details }}</p>
            <p>{{ experience.start_date }} - {{ experience.end_date }}</p>
          </div>
          <!-- <p>{{ job_title }}</p> -->
          <!-- <p>{{ experiences[0] }}</p> -->
        </div>
      </div>
    </span>
    <span class="border border-bottom-0">
      <div class="shadow-lg p-3 mb-5 bg-body rounded">
        <div class="mx-auto" style="width: 900px">
          <h2>Skills</h2>
          <div v-for="skill in skills" v-bind:key="skill.id">{{ skill.skill_name }}</div>
          <!-- <p>{{ skill_name }}</p> -->
        </div>
      </div>
    </span>

    <span class="border border-bottom-0">
      <div class="shadow-lg p-3 mb-5 bg-body rounded">
        <div class="mx-auto" style="width: 900px">
          <div>
            <h3>{{ student.capstones[0].name }}</h3>
            <p>{{ student.capstones[0].description }}</p>
            <p>{{ student.capstones[0].url }}</p>
            <p>{{ student.capstones[0].screenshot }}</p>
            <img v-bind:src="student.capstones[0].screenshot" v-bind:alt="student.capstones.name" class="image-fit" />
          </div>
        </div>
      </div>
    </span>
    <span class="border border-bottom-0">
      <div class="shadow-lg p-3 mb-5 bg-body rounded">
        <div class="mx-auto" style="width: 900px">
          <a class="twitter-timeline" href="https://twitter.com/PhilosophyDose_?ref_src=twsrc%5Etfw">
            Tweets by PhilosophyDose_
          </a>
        </div>
      </div>
    </span>
  </div>
  <!-- </div> -->
</template>

<style>
.image-fit {
  height: 25%;
  width: 25%;
  object-fit: cover;
}
body {
  padding: 0px;
  margin: 0px;
}
span {
  width: 100px;
  background: white;
  font-size: 20px;
  color: black;
  text-align: left;
  margin: 120px;
}
div {
  margin-bottom: 30px;
  margin-top: 0px;
  margin-left: 30px;
  margin-right: 30px;
}
</style>
