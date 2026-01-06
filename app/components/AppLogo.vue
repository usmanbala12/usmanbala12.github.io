<script setup lang="ts">
// Logo component with handwritten-style initials
</script>

<template>
  <a href="#about" class="logo" aria-label="UB - Home">
    <img
      src="~/assets/images/logo.png"
      alt="UB Logo Image"
      class="logo-image"
    />
  </a>
</template>

<style scoped>
.logo {
  display: flex;
  align-items: center;
  text-decoration: none;
  transition: transform var(--transition-fast);
}

.logo:hover {
  transform: scale(1.05);
}

.logo-image {
  height: 48px;
  width: auto;
  object-fit: contain;
}

@media (max-width: 768px) {
  .logo-image {
    height: 40px;
  }
}
</style>
