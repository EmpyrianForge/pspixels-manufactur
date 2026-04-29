<template>
  <ImpressumPage v-if="isImpressum" />
  <DatenschutzPage v-else-if="isDatenschutz" />
  <div v-else id="root">
    <SiteHeader />
    <main>
      <HeroSection />
      <ValuePropsSection />
      <MaterialsSection />
      <CraftProcess />
      <AudienceSplit />
      <UseCasesSection />
      <SustainabilitySection />
      <FinalCtaSection />
    </main>
    <SiteFooter />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import SiteHeader from './components/SiteHeader.vue'
import HeroSection from './components/HeroSection.vue'
import ValuePropsSection from './components/ValuePropsSection.vue'
import MaterialsSection from './components/MaterialsSection.vue'
import CraftProcess from './components/CraftProcess.vue'
import AudienceSplit from './components/AudienceSplit.vue'
import UseCasesSection from './components/UseCasesSection.vue'
import SustainabilitySection from './components/SustainabilitySection.vue'
import FinalCtaSection from './components/FinalCtaSection.vue'
import SiteFooter from './components/SiteFooter.vue'
import ImpressumPage from './components/ImpressumPage.vue'
import DatenschutzPage from './components/DatenschutzPage.vue'

const isImpressum = ref(window.location.hash === '#impressum')
const isDatenschutz = ref(window.location.hash === '#datenschutz')

function onHashChange() {
  isImpressum.value = window.location.hash === '#impressum'
  isDatenschutz.value = window.location.hash === '#datenschutz'
  if (!isImpressum.value && !isDatenschutz.value) {
    // Re-register scroll reveal after returning to main page
    requestAnimationFrame(initReveal)
  }
}

function initReveal() {
  const revealEls = document.querySelectorAll('.reveal:not(.is-visible)')
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.12, rootMargin: '0px 0px -40px 0px' }
  )
  revealEls.forEach((el) => observer.observe(el))
}

onMounted(() => {
  initReveal()
  window.addEventListener('hashchange', onHashChange)
})

onUnmounted(() => {
  window.removeEventListener('hashchange', onHashChange)
})
</script>

<style>
/* Global smooth scroll already in style.css */
#root {
  min-height: 100vh;
}
</style>
