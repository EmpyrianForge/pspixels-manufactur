<template>
  <header :class="['site-header', { 'is-scrolled': scrolled }]">
    <div class="header-inner">
      <a href="#" class="logo">Pspixels Studio</a>

      <nav class="nav-desktop" aria-label="Hauptnavigation">
        <a href="#materialien">Materialien</a>
        <a href="#fertigung">Fertigung</a>
        <a href="#referenzen">Referenzen</a>
        <a href="#kontakt">Kontakt</a>
        <a href="#kontakt" class="btn-outline">Anfragen</a>
      </nav>

      <button
        class="hamburger"
        :class="{ 'is-open': menuOpen }"
        @click="menuOpen = !menuOpen"
        aria-label="Menü öffnen"
        :aria-expanded="menuOpen"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>

    <nav v-if="menuOpen" class="nav-mobile" aria-label="Mobilnavigation">
      <a href="#materialien" @click="menuOpen = false">Materialien</a>
      <a href="#fertigung" @click="menuOpen = false">Fertigung</a>
      <a href="#referenzen" @click="menuOpen = false">Referenzen</a>
      <a href="#kontakt" @click="menuOpen = false">Kontakt</a>
      <a href="#kontakt" class="btn-outline" @click="menuOpen = false">Anfragen</a>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)
const menuOpen = ref(false)

function onScroll() {
  scrolled.value = window.scrollY > 40
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>

<style scoped>
.site-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  transition: background 0.35s ease, box-shadow 0.35s ease;
}

.site-header.is-scrolled {
  background: rgba(245, 239, 228, 0.96);
  backdrop-filter: blur(8px);
  box-shadow: 0 1px 0 var(--line);
}

.header-inner {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 2rem;
  height: 68px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-style: italic;
  font-variant: small-caps;
  font-size: 1.15rem;
  font-weight: 500;
  letter-spacing: 0.04em;
  color: var(--text);
}

.nav-desktop {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-desktop a {
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-muted);
  transition: color 0.2s;
}

.nav-desktop a:hover {
  color: var(--text);
}

.btn-outline {
  border: 1px solid var(--text);
  padding: 0.45rem 1.1rem;
  font-size: 0.75rem !important;
  letter-spacing: 0.1em !important;
  text-transform: uppercase;
  color: var(--text) !important;
  transition: background 0.2s, color 0.2s !important;
}

.btn-outline:hover {
  background: var(--text);
  color: var(--white) !important;
}

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}

.hamburger span {
  display: block;
  width: 22px;
  height: 1.5px;
  background: var(--text);
  transition: transform 0.25s ease, opacity 0.25s ease;
  transform-origin: center;
}

.hamburger.is-open span:nth-child(1) { transform: translateY(6.5px) rotate(45deg); }
.hamburger.is-open span:nth-child(2) { opacity: 0; }
.hamburger.is-open span:nth-child(3) { transform: translateY(-6.5px) rotate(-45deg); }

.nav-mobile {
  background: rgba(245, 239, 228, 0.98);
  border-top: 1px solid var(--line);
  display: flex;
  flex-direction: column;
  padding: 1.5rem 2rem 2rem;
  gap: 1.25rem;
}

.nav-mobile a {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-muted);
}

.nav-mobile .btn-outline {
  align-self: flex-start;
  margin-top: 0.5rem;
}

@media (max-width: 768px) {
  .nav-desktop { display: none; }
  .hamburger { display: flex; }
}
</style>
