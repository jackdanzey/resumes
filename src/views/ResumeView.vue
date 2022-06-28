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
      created: function () {},
      methods: {},
    };
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ students.first_name }} {{ students.last_name }}</h1>
    <h3>{{ students.email }}</h3>
    <h3>{{ students.phone_number }}</h3>
    <h3></h3>
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
  </div>
</template>

<style></style>
