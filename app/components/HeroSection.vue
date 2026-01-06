<script setup lang="ts">
// No extra props needed for now
</script>

<template>
  <section id="about" class="hero-section">
    <!-- Decorative watercolor blobs -->
    <div
      class="watercolor-blob watercolor-blob--peach hero-blob-1"
      aria-hidden="true"
    />
    <div
      class="watercolor-blob watercolor-blob--orange hero-blob-2"
      aria-hidden="true"
    />
    <div
      class="watercolor-blob watercolor-blob--green hero-blob-3"
      aria-hidden="true"
    />

    <div class="container hero-content">
      <!-- Portrait -->
      <div class="portrait-container">
        <div class="portrait-frame">
          <img
            src="~/assets/images/usman-bala.jpg"
            alt="Portrait of Usman Bala - Software Engineer"
            class="portrait-image"
          />
        </div>
      </div>

      <!-- Text content -->
      <h1 class="hero-name">Usman Bala</h1>
      <p class="hero-tagline">Software Engineer. Innovator. Problem Solver.</p>

      <p class="hero-bio">
        Passionate software engineer with strong foundations in core computing
        principles and industry experience in distributed systems, cloud-native
        architectures, and AI-driven applications. Skilled in building scalable
        backend solutions and integrating intelligent components into software
        systems.
      </p>

      <!-- CV Button -->
      <WatercolorButton
        href="/CV Usman Bala.pdf"
        variant="primary"
        size="lg"
        :download="true"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="20"
          height="20"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
          aria-hidden="true"
        >
          <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" />
          <polyline points="7 10 12 15 17 10" />
          <line x1="12" y1="15" x2="12" y2="3" />
        </svg>
        Download Full CV
      </WatercolorButton>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: calc(var(--header-height) + var(--spacing-md));
  padding-bottom: var(--spacing-lg);
  position: relative;
  overflow: hidden;
}

.hero-content {
  text-align: center;
  max-width: 800px;
}

/* Decorative blobs */
.hero-blob-1 {
  width: 300px;
  height: 300px;
  top: 10%;
  left: -100px;
}

.hero-blob-2 {
  width: 200px;
  height: 200px;
  top: 60%;
  right: -50px;
}

.hero-blob-3 {
  width: 250px;
  height: 250px;
  bottom: 5%;
  left: 30%;
}

/* Portrait */
.portrait-container {
  margin-bottom: var(--spacing-sm);
}

.portrait-frame {
  width: 220px;
  height: 220px;
  margin: 0 auto;
  border-radius: 50%;
  padding: 5px;
  background: linear-gradient(
    135deg,
    var(--color-accent) 0%,
    var(--color-secondary) 50%,
    var(--color-accent) 100%
  );
  box-shadow: var(--shadow-lg);
}

.portrait-image {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid var(--color-background);
}

.photo-credit {
  font-size: 0.75rem;
  color: var(--color-text-muted);
  margin-top: var(--spacing-xs);
  font-style: italic;
}

/* Hero text */
.hero-name {
  font-family: var(--font-body);
  font-size: clamp(1.25rem, 3.5vw, 2.25rem);
  font-weight: 700;
  color: var(--color-primary);
  margin-bottom: var(--spacing-xs);
  line-height: 1.1;
}

.hero-tagline {
  font-family: var(--font-body);
  font-size: clamp(0.75rem, 2.5vw, 1rem);
  font-weight: 500;
  color: var(--color-accent);
  margin-bottom: var(--spacing-sm);
}

.hero-bio {
  font-size: 0.9rem;
  line-height: 1.6;
  color: var(--color-text-muted);
  max-width: 520px;
  margin: 0 auto var(--spacing-sm);
}

@media (max-width: 768px) {
  .hero-section {
    padding-top: calc(var(--header-height) + var(--spacing-lg));
  }

  .portrait-frame {
    width: 180px;
    height: 180px;
  }

  .hero-bio {
    font-size: 1rem;
    padding: 0 var(--spacing-sm);
  }
}

@media (max-width: 480px) {
  .portrait-frame {
    width: 150px;
    height: 150px;
  }
}
</style>
