<script>
export default {
  data: function () {
    return {
      message: "RESUME! xxxxx",
      students: {
        first_name: "Jack",
        last_name: "Danzey",
        email: "jack@test.com",
        phone_number: "2225551111",
        short_bio: "Actualize student",
        linkedIn_url: "linkedin.com/jack",
        twitter: "@jackdanzey",
        personal_blog_url: "jack.com",
        resume: "resume.url",
        github_url: "github.com/jackdanzey",
        photo: "jack.jpg",
      },
      capstone: {
        name: "Super cool fun app",
        description: "Way cool app that is fun and everything",
        url: "www.coolapp.com",
        screenshot: "cool.jpg",
      },
      nameFilter: "",
    };
  },
  created: function () {},
  methods: {
    filterName: function () {
      return this.students.filter((student) => {
        let lowerName = student.first_name.toLowerCase();
        let lowerNameFilter = this.nameFilter.toLowerCase();
        return lowerName.includes(lowerNameFilter);
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <div v-for="student in filterName()" v-bind:key="student.id">
      <h2>{{ student.first_name }}</h2>
      <p>{{ student.last_name }}</p>
      <router-link v-bind:to="`/students/${student.id}`">More details</router-link>
    </div>
    <h1>{{ students.first_name }} {{ students.last_name }}</h1>
    <h3>{{ students.email }}</h3>
    <h3>{{ students.phone_number }}</h3>
    <h3></h3>
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

<style></style>
