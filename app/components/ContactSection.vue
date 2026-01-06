<script setup lang="ts">
interface SocialLink {
  name: string;
  href: string;
  icon: string;
}

defineProps<{
  socialLinks: SocialLink[];
}>();
</script>

<template>
  <section id="contact" class="contact-section">
    <!-- Watercolor wave decoration -->
    <div class="contact-wave" aria-hidden="true" />

    <div class="container contact-content">
      <h2 class="section-title">Get In Touch</h2>

      <p class="contact-text">
        I'm always open to discussing new projects, creative ideas, or
        opportunities to be part of your vision. Feel free to reach out!
      </p>

      <!-- Email -->
      <a href="mailto:contact.usmausman@gmail.com" class="contact-email">
        contact.usmausman@gmail.com
      </a>

      <!-- Social Links -->
      <div class="social-links">
        <a
          v-for="social in socialLinks"
          :key="social.name"
          :href="social.href"
          :aria-label="social.name"
          class="social-link"
          target="_blank"
          rel="noopener noreferrer"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="currentColor"
            aria-hidden="true"
          >
            <path :d="social.icon" />
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  position: relative;
  background: var(--color-background);
  padding-top: var(--spacing-3xl);
  padding-bottom: var(--spacing-2xl);
}

.contact-wave {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 60px;
  background: linear-gradient(
    90deg,
    transparent 0%,
    var(--color-secondary) 20%,
    var(--color-accent) 50%,
    var(--color-secondary) 80%,
    transparent 100%
  );
  filter: blur(20px);
  opacity: 0.3;
}

.contact-content {
  text-align: center;
  max-width: 600px;
}

.contact-text {
  font-size: 1.1rem;
  color: var(--color-text-muted);
  margin-bottom: var(--spacing-lg);
}

.contact-email {
  display: inline-block;
  font-family: var(--font-heading);
  font-size: clamp(1rem, 3vw, 1.5rem);
  color: var(--color-primary);
  text-decoration: none;
  padding: var(--spacing-sm) var(--spacing-md);
  border-radius: var(--radius-md);
  transition: all var(--transition-normal);
  margin-bottom: var(--spacing-xl);
}

.contact-email:hover {
  background: var(--color-text);
  color: var(--color-background);
}

/* Social Links */
.social-links {
  display: flex;
  justify-content: center;
  gap: var(--spacing-md);
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: var(--color-secondary);
  color: var(--color-primary);
  transition: all var(--transition-normal);
}

.social-link:hover {
  background: var(--color-accent);
  color: var(--color-primary);
  transform: translateY(-4px);
  box-shadow: var(--shadow-watercolor);
}

@media (max-width: 768px) {
  .social-link {
    width: 44px;
    height: 44px;
  }
}

@media (max-width: 480px) {
  .contact-email {
    font-size: 1.25rem;
    word-break: break-word;
  }
}
</style>
