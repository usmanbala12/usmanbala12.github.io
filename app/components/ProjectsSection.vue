<script setup lang="ts">
interface Project {
  title: string;
  description: string;
  image: string;
  imageAlt: string;
  year: string;
  techStack: string;
  link: string;
}

defineProps<{
  projects: Project[];
}>();
</script>

<template>
  <section id="projects" class="projects-section">
    <!-- Decorative elements -->
    <div
      class="watercolor-blob watercolor-blob--secondary projects-blob-1"
      aria-hidden="true"
    />
    <div
      class="watercolor-blob watercolor-blob--accent projects-blob-2"
      aria-hidden="true"
    />
    <div
      class="watercolor-blob watercolor-blob--primary projects-blob-3"
      aria-hidden="true"
    />

    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Projects</h2>
        <p class="section-subtitle">
          A collection of projects where code meets creativity
        </p>
      </div>

      <div class="projects-grid">
        <ProjectCard
          v-for="(project, index) in projects"
          :key="project.title"
          v-bind="project"
          class="animate-fade-in-up"
          :style="{ animationDelay: `${index * 0.15 + 0.2}s` }"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  background: var(--color-background);
  position: relative;
  padding: var(--spacing-3xl) 0;
  overflow: hidden;
}

.section-header {
  text-align: center;
  margin-bottom: var(--spacing-2xl);
}

.section-subtitle {
  color: var(--color-text-muted);
  font-size: 1.1rem;
  margin-top: calc(var(--spacing-xs) * -1);
}

/* Decorative Blobs */
.projects-blob-1 {
  width: 500px;
  height: 500px;
  top: -100px;
  right: -200px;
  background: var(--color-secondary);
  opacity: 0.2;
}

.projects-blob-2 {
  width: 400px;
  height: 400px;
  bottom: 10%;
  left: -150px;
  background: var(--color-accent);
  opacity: 0.15;
}

.projects-blob-3 {
  width: 300px;
  height: 300px;
  top: 40%;
  right: 15%;
  background: var(--color-primary);
  opacity: 0.05;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: var(--spacing-xl);
  perspective: 1000px;
}

@media (min-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
  }
}
</style>
