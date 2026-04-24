<template>
  <section class="sustainability">
    <div class="sustainability-inner">
      <div class="sustainability-header reveal">
        <p class="section-label">Verantwortung</p>
        <h2 class="section-title">Hergestellt, um zu bleiben.</h2>
        <p class="section-intro">
          Kein Greenwashing. Nur ein ehrlicher Anspruch: Weniger, aber besser.
        </p>
      </div>

      <div class="points">
        <article
          v-for="(point, index) in points"
          :key="index"
          class="point reveal"
          :style="{ transitionDelay: `${index * 0.12}s` }"
        >
          <div class="point-marker" aria-hidden="true"></div>
          <div class="point-content">
            <h3 class="point-title">{{ point.title }}</h3>
            <p class="point-body">{{ point.body }}</p>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const points = [
  {
    title: 'Echte Materialien',
    body: 'Holz aus kontrollierten Quellen. Kein MDF, kein Furnier. Was Sie sehen, ist was das Objekt ist — innen wie außen.',
  },
  {
    title: 'Langlebige Gestaltung',
    body: 'Kein Trend, keine Saison. Objekte, die in zehn Jahren noch genauso relevant sind wie heute. Zeitlosigkeit ist die nachhaltigste Entscheidung.',
  },
  {
    title: 'Gezielter Materialeinsatz',
    body: 'Additive Fertigung bedeutet: kein Verschnitt. Das Relief entsteht exakt so groß wie nötig. Nicht mehr, nicht weniger.',
  },
]
</script>

<style scoped>
.sustainability {
  background: var(--bg);
  padding: 7rem 2rem;
  border-top: 1px solid var(--line);
}

.sustainability-inner {
  max-width: 1280px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 6rem;
  align-items: start;
}

.sustainability-header {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  position: sticky;
  top: 100px;
}

.section-label {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--accent-wood);
}

.section-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(1.8rem, 3vw, 2.5rem);
  font-weight: 500;
  color: var(--text);
  line-height: 1.2;
}

.section-intro {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  font-weight: 300;
  color: var(--text-muted);
  line-height: 1.7;
}

/* Points */
.points {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.point {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 2rem;
  padding: 2.5rem 0;
  border-top: 1px solid var(--line);
  align-items: start;
}

.point:last-child {
  border-bottom: 1px solid var(--line);
}

.point-marker {
  width: 8px;
  height: 8px;
  background: var(--primary);
  border-radius: 50%;
  margin-top: 0.4rem;
  flex-shrink: 0;
}

.point-content {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.point-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.5rem;
  font-weight: 500;
  color: var(--text);
}

.point-body {
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  color: var(--text-muted);
  line-height: 1.75;
}

@media (max-width: 1024px) {
  .sustainability-inner {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .sustainability-header {
    position: static;
  }
}

@media (max-width: 768px) {
  .sustainability {
    padding: 4rem 1.5rem;
  }
}
</style>
