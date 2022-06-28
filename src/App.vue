<template>
  <!-- This is not a comment -->
  <nav>
    <router-link to="/">Home</router-link>
    |
    <router-link to="/about">About</router-link>
    |
    <router-link to="/resume">Resume</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Tahoma, Verdana, Segoe, sans-serif;
  font-size: large;
}
</style>
