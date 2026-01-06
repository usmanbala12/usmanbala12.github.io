<script setup lang="ts">
interface Props {
  href?: string;
  variant?: "primary" | "secondary";
  size?: "sm" | "md" | "lg";
  download?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  variant: "primary",
  size: "md",
  download: false,
});

const tag = computed(() => (props.href ? "a" : "button"));
</script>

<template>
  <component
    :is="tag"
    :href="href"
    :download="download ? '' : undefined"
    class="watercolor-btn"
    :class="[`watercolor-btn--${variant}`, `watercolor-btn--${size}`]"
  >
    <span class="btn-content">
      <slot />
    </span>
    <span class="btn-watercolor-effect" aria-hidden="true"></span>
  </component>
</template>

<style scoped>
.watercolor-btn {
  position: relative;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-body);
  font-weight: 500;
  text-decoration: none;
  border: none;
  cursor: pointer;
  overflow: hidden;
  transition: all var(--transition-normal);
}

/* Sizes */
.watercolor-btn--sm {
  padding: 0.5rem 1.25rem;
  font-size: 0.875rem;
  border-radius: var(--radius-sm);
}

.watercolor-btn--md {
  padding: 0.75rem 1.75rem;
  font-size: 1rem;
  border-radius: var(--radius-md);
}

.watercolor-btn--lg {
  padding: 1rem 2.5rem;
  font-size: 1.125rem;
  border-radius: var(--radius-lg);
}

/* Primary variant */
.watercolor-btn--primary {
  background: var(--color-accent);
  color: var(--color-white);
}

.watercolor-btn--primary:hover {
  background: var(--color-accent-hover);
  transform: translateY(-2px);
  box-shadow: var(--shadow-watercolor);
}

.watercolor-btn--primary:active {
  transform: translateY(0);
}

/* Secondary variant */
.watercolor-btn--secondary {
  background: transparent;
  color: var(--color-primary);
  border: 2px solid var(--color-accent);
}

.watercolor-btn--secondary:hover {
  background: var(--color-secondary-light);
  border-color: var(--color-accent);
}

/* Content */
.btn-content {
  position: relative;
  z-index: 1;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

/* Watercolor effect - soft bleed on edges */
.btn-watercolor-effect {
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  border-radius: inherit;
  opacity: 0;
  transition: opacity var(--transition-fast);
  z-index: 0;
}

.watercolor-btn--primary .btn-watercolor-effect {
  background: radial-gradient(
    ellipse at 30% 50%,
    var(--color-secondary) 0%,
    transparent 70%
  );
}

.watercolor-btn:hover .btn-watercolor-effect {
  opacity: 0.4;
}

/* Focus state */
.watercolor-btn:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 4px;
}
</style>
