<template>
  <div id="root">
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
import { onMounted } from 'vue'
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

onMounted(() => {
  const revealEls = document.querySelectorAll('.reveal')

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
})
</script>

<style>
/* Global smooth scroll already in style.css */
#root {
  min-height: 100vh;
}
</style>
