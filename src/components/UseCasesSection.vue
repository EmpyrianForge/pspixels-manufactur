<template>
  <section id="referenzen" class="use-cases">
    <div class="use-cases-inner">
      <header class="section-header reveal">
        <p class="section-label">Anwendungen</p>
        <h2 class="section-title">Objekte im Raum.</h2>
      </header>

      <div class="tiles-grid">
        <article
          v-for="(tile, index) in tiles"
          :key="index"
          class="tile reveal"
          :style="{ transitionDelay: `${index * 0.08}s`, '--tile-bg': tile.bg }"
        >
          <div class="tile-inner">
            <p class="tile-category">{{ tile.category }}</p>
            <h3 class="tile-name">{{ tile.name }}</h3>
            <p class="tile-desc">{{ tile.desc }}</p>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const tiles = [
  {
    name: 'Hotel & Hospitality',
    category: 'Gastronomie',
    desc: 'Empfangsbereiche und Lobbys, die Gäste mit dem Ort verbinden. Lokale Topografie als stilles Statement.',
    bg: 'linear-gradient(135deg, #3d2b1a 0%, #4a3320 100%)',
  },
  {
    name: 'Office & Empfang',
    category: 'Arbeitsraum',
    desc: 'Der Hauptsitz auf der Wand. Standorte, Märkte, Herkunft — räumlich und haptisch erfahrbar gemacht.',
    bg: 'linear-gradient(135deg, #2c2620 0%, #3a3028 100%)',
  },
  {
    name: 'Privater Wohnraum',
    category: 'Wohnen',
    desc: 'Keine Kunstdrucke. Ein Objekt mit Gewicht, Tiefe und Bedeutung. Der Lieblingsort als dauerhaftes Wandstück.',
    bg: 'linear-gradient(135deg, #4a3a2a 0%, #3d2b1a 100%)',
  },
  {
    name: 'Retail & Showroom',
    category: 'Handel',
    desc: 'Produkte, die Kunden berühren wollen. Die taktile Qualität eines Reliefs schafft Aufmerksamkeit ohne Lärm.',
    bg: 'linear-gradient(135deg, #302820 0%, #3d3028 100%)',
  },
  {
    name: 'Konferenz & Repräsentation',
    category: 'Business',
    desc: 'Ein Wandobjekt, das in Meetings gesehen wird. Das Gesprächsstoff schafft und Haltung zeigt.',
    bg: 'linear-gradient(135deg, #251e18 0%, #352a20 100%)',
  },
]
</script>

<style scoped>
.use-cases {
  background: var(--surface);
  padding: 7rem 2rem;
  border-top: 1px solid var(--line);
}

.use-cases-inner {
  max-width: 1280px;
  margin: 0 auto;
}

.section-header {
  margin-bottom: 3.5rem;
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

.section-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(2rem, 3.5vw, 3rem);
  font-weight: 500;
  color: var(--text);
}

/* Grid */
.tiles-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: auto auto;
  gap: 1px;
  background: var(--line);
  border: 1px solid var(--line);
}

/* 5 tiles: 3 top, 2 bottom centered */
.tile:nth-child(4) { grid-column: 1; }
.tile:nth-child(5) { grid-column: 2; }

.tile {
  background: var(--tile-bg, #3d2b1a);
  padding: 3rem 2.5rem 3rem;
  min-height: 280px;
  display: flex;
  flex-direction: column;
  position: relative;
  overflow: hidden;
  transition: transform 0.3s ease;
}

.tile::before {
  content: '';
  position: absolute;
  inset: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 3px,
    rgba(255,255,255,0.015) 3px,
    rgba(255,255,255,0.015) 4px
  );
  pointer-events: none;
}

.tile:hover {
  transform: scale(1.01);
  z-index: 1;
}

.tile-inner {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  height: 100%;
}

.tile-category {
  font-family: 'Inter', sans-serif;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--accent-light);
  opacity: 0.7;
}

.tile-name {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(1.6rem, 2.5vw, 2.2rem);
  font-weight: 500;
  color: #fdfaf6;
  line-height: 1.1;
  margin-top: auto;
}

.tile-desc {
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 300;
  color: #c4b49f;
  line-height: 1.7;
}

@media (max-width: 1024px) {
  .tiles-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  .tile:nth-child(4) { grid-column: auto; }
  .tile:nth-child(5) { grid-column: auto; }
}

@media (max-width: 768px) {
  .use-cases {
    padding: 4rem 1.5rem;
  }

  .tiles-grid {
    grid-template-columns: 1fr;
  }

  .tile {
    min-height: 220px;
    padding: 2rem 1.5rem;
  }
}
</style>
