<template>
  <section class="value-props">
    <div class="value-props-inner">
      <header class="section-header reveal">
        <p class="section-label">Warum Pspixels Studio</p>
      </header>

      <ol class="props-list">
        <li
          v-for="(prop, index) in props"
          :key="index"
          class="prop-item reveal"
          :style="{ transitionDelay: `${index * 0.1}s` }"
        >
          <span class="prop-number">0{{ index + 1 }}</span>
          <div class="prop-content">
            <h3 class="prop-title">{{ prop.title }}</h3>
            <p class="prop-desc">{{ prop.desc }}</p>
          </div>
        </li>
      </ol>

      <p class="props-tagline reveal">Wärme im Material. Präzision in der Form.</p>
    </div>
  </section>
</template>

<script setup>
const props = [
  {
    title: 'Echte Haptik',
    desc: 'Kein Dekor, kein Laminat. Sondern Holz mit natürlicher Maserung und spürbarer Oberfläche.',
  },
  {
    title: 'Präzise gefertigt',
    desc: 'Jede Höhenlinie sitzt genau dort, wo sie hingehört. Sauber gefertigt mit feiner Schichthöhe und klarer Kontur.',
  },
  {
    title: 'Individuell gestaltbar',
    desc: 'Jeder Ort, jedes Format, jede Wirkung. Von der Lieblingsinsel bis zum maßgefertigten Objekt.',
  },
  {
    title: 'Dauerhafter Wert',
    desc: 'Kein Saisonprodukt, sondern ein Objekt mit Dauer. Gemacht für Räume, die langfristig wirken sollen.',
  },
]
</script>

<style scoped>
.value-props {
  background: var(--bg);
  padding: 6rem 2rem;
  border-top: 1px solid var(--line);
}

.value-props-inner {
  max-width: 1280px;
  margin: 0 auto;
}

.section-header {
  margin-bottom: 3.5rem;
}

.section-label {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--accent-wood);
}

.props-list {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0;
  border-left: 1px solid var(--line);
}

.prop-item {
  padding: 2.5rem 2.5rem 2.5rem 2.5rem;
  border-right: 1px solid var(--line);
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.prop-number {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 3rem;
  font-weight: 400;
  color: var(--line);
  line-height: 1;
}

.prop-content {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.prop-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.5rem;
  font-weight: 500;
  color: var(--text);
}

.prop-desc {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  font-weight: 300;
  color: var(--text-muted);
  line-height: 1.7;
}

@media (max-width: 1024px) {
  .props-list {
    grid-template-columns: repeat(2, 1fr);
  }
  .prop-item:nth-child(2n) {
    border-right: none;
  }
  .prop-item:nth-child(n+3) {
    border-top: 1px solid var(--line);
  }
}

.props-tagline {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(1.1rem, 2vw, 1.5rem);
  font-style: italic;
  font-weight: 400;
  color: var(--text-muted);
  text-align: center;
  padding: 3rem 0 0;
  letter-spacing: 0.02em;
}

@media (max-width: 768px) {
  .value-props {
    padding: 4rem 1.5rem;
  }

  .props-list {
    grid-template-columns: 1fr;
    border-left: none;
  }

  .prop-item {
    padding: 2rem 0;
    border-right: none;
    border-top: 1px solid var(--line);
  }

  .prop-item:last-child {
    border-bottom: 1px solid var(--line);
  }
}
</style>
