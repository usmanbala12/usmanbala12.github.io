<script setup lang="ts">
import projectsData from "./data/projects.json";
import socialsData from "./data/socials.json";
</script>

<template>
  <div class="app">
    <AppHeader />

    <main>
      <HeroSection />
      <ProjectsSection :projects="projectsData" />
      <ContactSection :social-links="socialsData" />
    </main>

    <AppFooter />
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
}
</style>
