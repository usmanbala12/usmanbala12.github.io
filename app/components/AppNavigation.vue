<script setup lang="ts">
interface NavItem {
  label: string;
  href: string;
}

const navItems: NavItem[] = [
  { label: "About", href: "#about" },
  { label: "Projects", href: "#projects" },
  { label: "Contact", href: "#contact" },
];

const activeSection = ref("about");
const isMobileMenuOpen = ref(false);

// Scroll spy to track active section
const updateActiveSection = () => {
  const sections = ["about", "projects", "contact"];
  const scrollPosition = window.scrollY + 150;

  for (const sectionId of sections) {
    const section = document.getElementById(sectionId);
    if (section) {
      const { offsetTop, offsetHeight } = section;
      if (
        scrollPosition >= offsetTop &&
        scrollPosition < offsetTop + offsetHeight
      ) {
        activeSection.value = sectionId;
        break;
      }
    }
  }
};

const handleNavClick = () => {
  isMobileMenuOpen.value = false;
  // Smooth scroll is handled by CSS
};

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

onMounted(() => {
  window.addEventListener("scroll", updateActiveSection);
  updateActiveSection();
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateActiveSection);
});
</script>

<template>
  <nav class="navigation" role="navigation" aria-label="Main navigation">
    <!-- Desktop Navigation -->
    <ul class="nav-list">
      <li v-for="item in navItems" :key="item.href" class="nav-item">
        <a
          :href="item.href"
          class="nav-link"
          :class="{ 'nav-link--active': activeSection === item.href.slice(1) }"
          @click="handleNavClick()"
        >
          {{ item.label }}
          <span class="nav-link-underline" aria-hidden="true" />
        </a>
      </li>
    </ul>

    <!-- Mobile Menu Button -->
    <button
      class="mobile-menu-btn"
      :class="{ 'mobile-menu-btn--open': isMobileMenuOpen }"
      aria-label="Toggle navigation menu"
      :aria-expanded="isMobileMenuOpen"
      aria-controls="mobile-nav"
      @click="toggleMobileMenu"
    >
      <span class="hamburger-line" />
      <span class="hamburger-line" />
      <span class="hamburger-line" />
    </button>

    <!-- Mobile Navigation Drawer -->
    <div
      id="mobile-nav"
      class="mobile-nav"
      :class="{ 'mobile-nav--open': isMobileMenuOpen }"
    >
      <ul class="mobile-nav-list">
        <li v-for="item in navItems" :key="item.href" class="mobile-nav-item">
          <a
            :href="item.href"
            class="mobile-nav-link"
            :class="{
              'mobile-nav-link--active': activeSection === item.href.slice(1),
            }"
            @click="handleNavClick()"
          >
            {{ item.label }}
          </a>
        </li>
      </ul>
    </div>

    <!-- Mobile overlay -->
    <div
      v-if="isMobileMenuOpen"
      class="mobile-overlay"
      @click="isMobileMenuOpen = false"
    />
  </nav>
</template>

<style scoped>
.navigation {
  display: flex;
  align-items: center;
}

/* Desktop Navigation */
.nav-list {
  display: flex;
  list-style: none;
  gap: var(--spacing-lg);
  margin: 0;
  padding: 0;
}

.nav-link {
  position: relative;
  font-family: var(--font-body);
  font-size: 1rem;
  font-weight: 500;
  color: var(--color-primary);
  text-decoration: none;
  padding: 0.5rem 0;
  transition: color var(--transition-fast);
}

.nav-link:hover {
  color: var(--color-accent);
}

.nav-link-underline {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 3px;
  background: linear-gradient(
    90deg,
    var(--color-accent),
    var(--color-secondary)
  );
  border-radius: 2px;
  filter: blur(0.5px);
  transition: width var(--transition-normal);
}

.nav-link:hover .nav-link-underline,
.nav-link--active .nav-link-underline {
  width: 100%;
}

.nav-link--active {
  color: var(--color-accent);
}

/* Mobile Menu Button */
.mobile-menu-btn {
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 5px;
  width: 40px;
  height: 40px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 8px;
  z-index: 1001;
}

.hamburger-line {
  display: block;
  width: 24px;
  height: 2px;
  background-color: var(--color-primary);
  border-radius: 2px;
  transition: all var(--transition-fast);
}

.mobile-menu-btn--open .hamburger-line:first-child {
  transform: rotate(45deg) translate(5px, 5px);
}

.mobile-menu-btn--open .hamburger-line:nth-child(2) {
  opacity: 0;
}

.mobile-menu-btn--open .hamburger-line:last-child {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Mobile Navigation Drawer */
.mobile-nav {
  display: none;
  position: fixed;
  top: 0;
  right: -280px;
  width: 280px;
  height: 100vh;
  background: var(--color-background);
  box-shadow: var(--shadow-lg);
  padding: calc(var(--header-height) + var(--spacing-lg)) var(--spacing-lg)
    var(--spacing-lg);
  transition: right var(--transition-normal);
  z-index: 1000;
}

.mobile-nav--open {
  right: 0;
}

.mobile-nav-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.mobile-nav-item {
  margin-bottom: var(--spacing-sm);
}

.mobile-nav-link {
  display: block;
  font-family: var(--font-body);
  font-size: 1.25rem;
  font-weight: 500;
  color: var(--color-primary);
  text-decoration: none;
  padding: var(--spacing-sm);
  border-radius: var(--radius-sm);
  transition: all var(--transition-fast);
}

.mobile-nav-link:hover,
.mobile-nav-link--active {
  background: var(--color-secondary-light);
  color: var(--color-accent);
}

.mobile-overlay {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 66, 37, 0.3);
  z-index: 999;
}

/* Responsive */
@media (max-width: 768px) {
  .nav-list {
    display: none;
  }

  .mobile-menu-btn {
    display: flex;
  }

  .mobile-nav {
    display: block;
  }

  .mobile-overlay {
    display: block;
  }
}
</style>
