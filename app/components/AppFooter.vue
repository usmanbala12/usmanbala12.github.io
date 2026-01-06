<script setup lang="ts">
// No extra logic needed
</script>

<template>
  <footer class="footer">
    <div class="footer-wave" aria-hidden="true" />
    <div class="container footer-content">
      <p class="footer-text">
        © {{ new Date().getFullYear() }} Usman Bala. Crafted with
        <span class="footer-heart" aria-label="love">♥</span>
        and a splash of watercolor.
      </p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  position: relative;
  background: var(--color-background);
  padding: var(--spacing-xl) 0 var(--spacing-lg);
  margin-top: var(--spacing-xl);
}

.footer-wave {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 40px;
  background: linear-gradient(
    90deg,
    var(--color-secondary) 0%,
    var(--color-accent) 25%,
    var(--color-secondary) 50%,
    var(--color-accent) 75%,
    var(--color-secondary) 100%
  );
  filter: blur(25px);
  opacity: 0.2;
}

.footer-content {
  text-align: center;
}

.footer-text {
  font-size: 0.9rem;
  color: var(--color-text-muted);
}

.footer-heart {
  color: var(--color-accent);
  display: inline-block;
  animation: heartbeat 1.5s ease infinite;
}

@keyframes heartbeat {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
}
</style>
