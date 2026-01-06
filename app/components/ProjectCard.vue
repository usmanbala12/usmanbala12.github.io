<script setup lang="ts">
interface Props {
  title: string;
  description: string;
  image: string;
  imageAlt: string;
  year: string;
  techStack: string;
  link: string;
}

defineProps<Props>();
</script>

<template>
  <article class="project-card">
    <!-- Watercolor effect background -->
    <div class="card-watercolor-bg" aria-hidden="true" />

    <!-- Organic border element -->
    <div class="card-border" aria-hidden="true" />

    <!-- Project Image -->
    <div class="card-image-container">
      <img :src="image" :alt="imageAlt" class="card-image" loading="lazy" />
      <div class="image-overlay" />
    </div>

    <!-- Project Content -->
    <div class="card-content">
      <div class="card-header">
        <h3 class="card-title">{{ title }}</h3>
        <span class="card-year">{{ year }}</span>
      </div>

      <p class="card-description">{{ description }}</p>

      <!-- Tech Stack -->
      <div class="card-tech">
        <span class="tech-badge">{{ techStack }}</span>
      </div>

      <!-- Link Button -->
      <div class="card-actions">
        <WatercolorButton
          :href="link"
          variant="secondary"
          size="sm"
          class="card-link"
        >
          Explore
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
            aria-hidden="true"
          >
            <path d="M5 12h14" />
            <polyline points="12 5 19 12 12 19" />
          </svg>
        </WatercolorButton>
      </div>
    </div>
  </article>
</template>

<style scoped>
.project-card {
  position: relative;
  background: var(--color-white);
  border-radius: var(--radius-lg);
  isolation: isolate;
  transition: all var(--transition-normal);
  display: flex;
  flex-direction: column;
  height: 100%;
  padding: var(--spacing-xs);
  box-shadow: var(--shadow-sm);
  border: 1px solid rgba(109, 148, 197, 0.1);
}

.project-card:hover {
  transform: translateY(-8px) rotate(1deg);
  box-shadow: var(--shadow-lg);
  border-color: var(--color-accent);
}

/* Watercolor background bleed */
.card-watercolor-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(
      circle at 80% 20%,
      rgba(203, 220, 235, 0.4) 0%,
      transparent 60%
    ),
    radial-gradient(
      circle at 20% 80%,
      rgba(109, 148, 197, 0.1) 0%,
      transparent 50%
    );
  filter: blur(20px);
  opacity: 0;
  transition: opacity var(--transition-normal);
  z-index: -1;
}

.project-card:hover .card-watercolor-bg {
  opacity: 1;
}

/* Organic border stroke */
.card-border {
  position: absolute;
  inset: -2px;
  border: 2px solid transparent;
  border-radius: inherit;
  pointer-events: none;
  z-index: 2;
  transition: border-color var(--transition-normal);
}

.project-card:hover .card-border {
  border-color: rgba(109, 148, 197, 0.3);
  mask-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.5' numOctaves='3'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
}

/* Image container */
.card-image-container {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 10;
  overflow: hidden;
  border-radius: var(--radius-md);
  margin-bottom: var(--spacing-sm);
}

.card-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform var(--transition-slow);
}

.project-card:hover .card-image {
  transform: scale(1.1);
}

.image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    transparent 60%,
    rgba(61, 90, 128, 0.2)
  );
  opacity: 0.5;
}

/* Content */
.card-content {
  padding: var(--spacing-sm);
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: var(--spacing-xs);
}

.card-title {
  font-family: var(--font-heading);
  font-size: 1.5rem;
  color: var(--color-primary);
}

.card-year {
  font-family: var(--font-body);
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--color-accent);
  opacity: 0.8;
}

.card-description {
  font-size: 0.95rem;
  color: var(--color-text-muted);
  line-height: 1.6;
  margin-bottom: var(--spacing-md);
}

/* Tech badge */
.card-tech {
  margin-top: auto;
  margin-bottom: var(--spacing-md);
}

.tech-badge {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  background: var(--color-secondary-light);
  color: var(--color-primary);
  font-size: 0.75rem;
  font-weight: 600;
  border-radius: var(--radius-sm);
  position: relative;
  overflow: hidden;
}

.tech-badge::before {
  content: "";
  position: absolute;
  inset: 0;
  background: radial-gradient(
    circle at 30% 50%,
    rgba(109, 148, 197, 0.2),
    transparent
  );
}

/* Action area */
.card-actions {
  display: flex;
  justify-content: flex-end;
}

@media (max-width: 768px) {
  .card-content {
    padding: var(--spacing-xs);
  }

  .card-title {
    font-size: 1.25rem;
  }
}
</style>
