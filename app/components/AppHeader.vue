<script setup lang="ts">
const isScrolled = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  handleScroll();
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <header
    class="header"
    :class="{ 'header--scrolled': isScrolled }"
    role="banner"
  >
    <div class="header-container">
      <AppLogo />
      <AppNavigation />
    </div>
  </header>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  height: var(--header-height);
  z-index: 100;
  transition: all var(--transition-normal);
}

.header::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(245, 245, 220, 0.85);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  opacity: 0;
  transition: opacity var(--transition-normal);
  z-index: -1;
}

.header--scrolled::before {
  opacity: 1;
}

.header--scrolled {
  box-shadow: 0 2px 20px rgba(0, 66, 37, 0.08);
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 var(--spacing-lg);
}

@media (max-width: 768px) {
  .header-container {
    padding: 0 var(--spacing-md);
  }
}
</style>
