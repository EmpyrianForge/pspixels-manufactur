<template>
  <section id="materialien" class="materials">
    <div class="materials-inner">

      <div class="material-panel wood-panel reveal">
        <div class="panel-content">
          <p class="panel-label">Material I</p>
          <h2 class="panel-headline">Walnuss.<br />Eiche.<br />Natur.</h2>
          <p class="panel-body">
            Jede Platte trägt eine Geschichte. Die Maserung entsteht über Jahrzehnte —
            sie ist kein Dekor, sondern Substanz. Wir verwenden ausgewählte Hölzer
            aus kontrollierten Quellen, geölt und nicht lackiert.
          </p>
          <ul class="panel-list">
            <li>Walnuss (amerikanisch, europäisch)</li>
            <li>Eiche (hell, geräuchert)</li>
            <li>Esche, Ahorn auf Anfrage</li>
          </ul>
        </div>
        <div class="wood-texture-strip" aria-hidden="true">
          <div class="grain-line" v-for="i in 8" :key="i" :style="{ top: `${8 + i * 11}%`, opacity: 0.15 + (i % 3) * 0.07 }"></div>
        </div>
      </div>

      <div class="material-panel print-panel reveal" style="transition-delay: 0.15s">
        <div class="panel-content">
          <p class="panel-label">Material II</p>
          <h2 class="panel-headline">Präzision.<br />Form.<br />Freiheit.</h2>
          <p class="panel-body">
            Additive Fertigung bedeutet: kein Abtrag, kein Verschnitt, keine Kompromisse
            bei der Form. Das Relief entsteht Schicht für Schicht aus weißem PLA —
            matt, leicht, dauerhaft.
          </p>
          <ul class="panel-list">
            <li>Schichthöhe 0,1 mm</li>
            <li>Weißes/crème PLA, matte Oberfläche</li>
            <li>Verbindung mechanisch — kein Kleber</li>
          </ul>
        </div>
        <div class="print-texture-strip" aria-hidden="true">
          <div class="layer-line" v-for="i in 14" :key="i" :style="{ top: `${3 + i * 6.5}%` }"></div>
        </div>
      </div>

    </div>

    <div class="synthesis reveal">
      <p class="synthesis-text">Keine Imitation. Eine bewusste Synthese.</p>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.materials {
  background: var(--surface);
  overflow: hidden;
}

.materials-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 580px;
}

/* Wood panel */
.wood-panel {
  background: linear-gradient(135deg, #4a3320 0%, #3d2b1a 40%, #2c1e10 100%);
  position: relative;
  overflow: hidden;
}

.wood-panel .panel-label { color: #c9a87c; }
.wood-panel .panel-headline { color: #fdfaf6; }
.wood-panel .panel-body { color: #c4b49f; }
.wood-panel .panel-list { color: #a08060; }

.wood-texture-strip {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.grain-line {
  position: absolute;
  left: 0;
  right: 0;
  height: 1px;
  background: #8a6a45;
  transform: skewY(-0.5deg);
}

/* Print panel */
.print-panel {
  background: linear-gradient(135deg, #f8f5f0 0%, #ede8e0 50%, #e4ddd2 100%);
  position: relative;
  overflow: hidden;
  border-left: 1px solid var(--line);
}

.print-panel .panel-label { color: var(--accent-wood); }
.print-panel .panel-headline { color: var(--text); }
.print-panel .panel-body { color: var(--text-muted); }
.print-panel .panel-list { color: var(--text-muted); }

.print-texture-strip {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.layer-line {
  position: absolute;
  left: 0;
  right: 0;
  height: 1px;
  background: var(--line);
  opacity: 0.5;
}

/* Shared panel styles */
.panel-content {
  position: relative;
  z-index: 1;
  padding: 4rem 3.5rem;
  height: 100%;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.panel-label {
  font-family: 'Inter', sans-serif;
  font-size: 0.68rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.panel-headline {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(2.5rem, 4vw, 3.5rem);
  font-weight: 500;
  line-height: 1.1;
}

.panel-body {
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  line-height: 1.75;
  max-width: 38ch;
}

.panel-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
  margin-top: auto;
  padding-top: 1rem;
}

.panel-list li {
  font-family: 'Inter', sans-serif;
  font-size: 0.78rem;
  letter-spacing: 0.04em;
  padding-left: 1rem;
  position: relative;
}

.panel-list li::before {
  content: '—';
  position: absolute;
  left: 0;
  opacity: 0.5;
}

/* Synthesis */
.synthesis {
  background: var(--accent-dark);
  padding: 2.5rem 3.5rem;
  text-align: center;
}

.synthesis-text {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(1.3rem, 2.5vw, 2rem);
  font-style: italic;
  font-weight: 400;
  color: var(--accent-light);
  letter-spacing: 0.02em;
}

@media (max-width: 768px) {
  .materials-inner {
    grid-template-columns: 1fr;
  }

  .print-panel {
    border-left: none;
    border-top: 1px solid var(--line);
  }

  .panel-content {
    padding: 3rem 1.5rem;
  }

  .synthesis {
    padding: 2rem 1.5rem;
  }
}
</style>
