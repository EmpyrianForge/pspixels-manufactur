<template>
  <section id="fertigung" class="craft-process">
    <div class="craft-inner">
      <header class="craft-header reveal">
        <p class="section-label">Herstellung</p>
        <h2 class="craft-title">Von der Idee zum Objekt.</h2>
      </header>

      <div class="steps-container">
        <ol class="steps-list">
          <li
            v-for="(step, index) in steps"
            :key="index"
            class="step reveal"
            :style="{ transitionDelay: `${index * 0.12}s` }"
          >
            <div class="step-number">{{ String(index + 1).padStart(2, '0') }}</div>
            <div class="step-connector" v-if="index < steps.length - 1" aria-hidden="true"></div>
            <div class="step-body">
              <h3 class="step-title">{{ step.title }}</h3>
              <p class="step-desc">{{ step.desc }}</p>
            </div>
          </li>
        </ol>
      </div>
    </div>
  </section>
</template>

<script setup>
const steps = [
  {
    title: 'Materialauswahl',
    desc: 'Handverlesene Hölzer aus kontrollierten Quellen. Jede Platte wird auf Maserung, Feuchte und Dichte geprüft.',
  },
  {
    title: 'Digitale Konstruktion',
    desc: 'Topografiedaten werden aufbereitet und zu präzisen 3D-Modellen verarbeitet. Maßstab, Höhenexponent und Format nach Wunsch.',
  },
  {
    title: 'Additive Fertigung',
    desc: 'Schicht für Schicht. 0,1 mm Auflösung. Das Relief entsteht in einem Stück — keine Nachbearbeitung der Form nötig.',
  },
  {
    title: 'Veredelung & Montage',
    desc: 'Schleifen, Ölen, Verbinden. Das Relief wird passgenau auf das Holz gesetzt. Signiert, verpackt, versendet.',
  },
]
</script>

<style scoped>
.craft-process {
  background: var(--bg);
  padding: 7rem 2rem;
  border-top: 1px solid var(--line);
}

.craft-inner {
  max-width: 1280px;
  margin: 0 auto;
}

.craft-header {
  margin-bottom: 4rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.section-label {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--accent-wood);
}

.craft-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(2rem, 3.5vw, 3rem);
  font-weight: 500;
  color: var(--text);
}

/* Steps */
.steps-container {
  overflow-x: auto;
}

.steps-list {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0;
  position: relative;
}

/* Horizontal connector line behind all steps */
.steps-list::before {
  content: '';
  position: absolute;
  top: 22px;
  left: 5%;
  right: 5%;
  height: 1px;
  background: var(--line);
  z-index: 0;
}

.step {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  padding: 0 2rem 0 0;
  position: relative;
}

.step-number {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 0.95rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  color: var(--white);
  background: var(--primary);
  width: 44px;
  height: 44px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 1;
  flex-shrink: 0;
}

.step-body {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  padding-top: 0.5rem;
}

.step-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.35rem;
  font-weight: 500;
  color: var(--text);
}

.step-desc {
  font-family: 'Inter', sans-serif;
  font-size: 0.82rem;
  font-weight: 300;
  color: var(--text-muted);
  line-height: 1.75;
}

@media (max-width: 1024px) {
  .steps-list {
    grid-template-columns: repeat(2, 1fr);
    gap: 3rem 2rem;
  }
  .steps-list::before { display: none; }
}

@media (max-width: 768px) {
  .craft-process {
    padding: 4rem 1.5rem;
  }

  .steps-list {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }

  .step {
    flex-direction: row;
    align-items: flex-start;
    padding: 0;
    gap: 1.25rem;
  }

  .step-number {
    flex-shrink: 0;
  }

  .step-body {
    padding-top: 0.7rem;
  }
}
</style>
