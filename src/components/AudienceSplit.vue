<template>
  <section class="audience">
    <div class="audience-inner">

      <article class="audience-panel b2b reveal">
        <div class="panel-inner">
          <p class="panel-eyebrow">Für Professionals</p>
          <h2 class="panel-title">Räume, die<br />Haltung zeigen.</h2>
          <p class="panel-intro">
            Ein Objekt, das Kunden beim Eintreten bemerken. Das Gespräche auslöst.
            Das Ihren Anspruch an Materialität sichtbar macht.
          </p>
          <ul class="use-list">
            <li>Architektur &amp; Planungsbüros</li>
            <li>Interior Design &amp; Hospitality</li>
            <li>Showrooms &amp; Flagshipstores</li>
            <li>Empfangsbereiche &amp; Konferenzräume</li>
          </ul>
          <a href="#kontakt" class="panel-cta">Anfrage stellen</a>
        </div>
      </article>

      <article class="audience-panel private reveal" style="transition-delay: 0.15s">
        <div class="panel-inner">
          <p class="panel-eyebrow">Für Liebhaber</p>
          <h2 class="panel-title">Ein Ort.<br />Dauerhaft.</h2>
          <p class="panel-intro">
            Der Berg, an dem man aufgewachsen ist. Die Küste des ersten Urlaubs.
            Karten, die nicht im Regal stehen, sondern an der Wand hängen.
          </p>
          <ul class="use-list">
            <li>Private Wohnräume &amp; Lofts</li>
            <li>Persönliche Geschenke für Sammler</li>
            <li>Heimatbezug &amp; Erinnerungsorte</li>
            <li>Designaffine Haushalte</li>
          </ul>
          <a href="#kontakt" class="panel-cta">Objekt anfragen</a>
        </div>
      </article>

    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.audience {
  background: var(--bg);
  border-top: 1px solid var(--line);
}

.audience-inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  max-width: 1280px;
  margin: 0 auto;
}

.audience-panel {
  padding: 5rem 4rem;
  display: flex;
  flex-direction: column;
}

.b2b {
  background: var(--surface);
  border-right: 1px solid var(--line);
}

.private {
  background: var(--surface-2);
}

.panel-inner {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
  height: 100%;
}

.panel-eyebrow {
  font-family: 'Inter', sans-serif;
  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--accent-wood);
}

.panel-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(2rem, 3.5vw, 3rem);
  font-weight: 500;
  line-height: 1.1;
  color: var(--text);
}

.panel-intro {
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  color: var(--text-muted);
  line-height: 1.75;
  max-width: 36ch;
}

.use-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.55rem;
  margin-top: 0.5rem;
}

.use-list li {
  font-family: 'Inter', sans-serif;
  font-size: 0.82rem;
  color: var(--text-muted);
  padding-left: 1.1rem;
  position: relative;
}

.use-list li::before {
  content: '→';
  position: absolute;
  left: 0;
  font-size: 0.7rem;
  color: var(--accent-light);
}

.panel-cta {
  display: inline-block;
  margin-top: auto;
  padding-top: 1.75rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.78rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--primary);
  border-bottom: 1px solid var(--primary);
  padding-bottom: 2px;
  align-self: flex-start;
  transition: color 0.2s, border-color 0.2s;
}

.panel-cta:hover {
  color: var(--primary-hover);
  border-color: var(--primary-hover);
}

@media (max-width: 768px) {
  .audience-inner {
    grid-template-columns: 1fr;
  }

  .b2b {
    border-right: none;
    border-bottom: 1px solid var(--line);
  }

  .audience-panel {
    padding: 3.5rem 1.5rem;
  }
}
</style>
