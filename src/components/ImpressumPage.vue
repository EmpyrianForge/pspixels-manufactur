<template>
  <div class="impressum-page">
    <header class="imp-header">
      <div class="imp-header-inner">
        <a href="/" class="imp-logo" @click.prevent="goHome">pspixels manufactur</a>
        <a href="/" class="imp-back" @click.prevent="goHome">← Zurück</a>
      </div>
    </header>

    <main class="imp-main">
      <div class="imp-inner">
        <h1 class="imp-title">Impressum</h1>

        <section class="imp-block">
          <h2>Angaben gemäß § 5 DDG</h2>
          <address>
            pspixels<br />
            Nino Parr<br />
            Amselweg 1<br />
            63829 Krombach<br />
            Deutschland
          </address>
        </section>

        <section class="imp-block">
          <h2>Kontakt</h2>
          <p>
            E-Mail:
            <a href="mailto:pspixels@gmx.de">pspixels@gmx.de</a>
          </p>
        </section>

        <section class="imp-block">
          <h2>Umsatzsteuer-Identifikationsnummer</h2>
          <p>
            Umsatzsteuer-Identifikationsnummer gemäß § 27a Umsatzsteuergesetz:<br />
            DE451528556
          </p>
        </section>

        <section class="imp-block">
          <h2>Verantwortlich für den Inhalt nach § 18 Abs. 2 MStV</h2>
          <address>
            Nino Parr<br />
            Amselweg 1<br />
            63829 Krombach<br />
            Deutschland
          </address>
        </section>

        <section class="imp-block">
          <h2>Haftung für Inhalte</h2>
          <p>
            Als Diensteanbieter sind wir gemäß § 7 Abs. 1 DDG für eigene Inhalte auf diesen Seiten
            nach den allgemeinen Gesetzen verantwortlich. Nach §§ 8 bis 10 DDG sind wir als
            Diensteanbieter jedoch nicht verpflichtet, übermittelte oder gespeicherte fremde
            Informationen zu überwachen oder nach Umständen zu forschen, die auf eine rechtswidrige
            Tätigkeit hinweisen. Verpflichtungen zur Entfernung oder Sperrung der Nutzung von
            Informationen nach den allgemeinen Gesetzen bleiben hiervon unberührt. Eine
            diesbezügliche Haftung ist jedoch erst ab dem Zeitpunkt der Kenntnis einer konkreten
            Rechtsverletzung möglich. Bei Bekanntwerden von entsprechenden Rechtsverletzungen
            werden wir diese Inhalte umgehend entfernen.
          </p>
        </section>

        <section class="imp-block">
          <h2>Haftung für Links</h2>
          <p>
            Unser Angebot enthält Links zu externen Websites Dritter, auf deren Inhalte wir keinen
            Einfluss haben. Deshalb können wir für diese fremden Inhalte auch keine Gewähr
            übernehmen. Für die Inhalte der verlinkten Seiten ist stets der jeweilige Anbieter oder
            Betreiber der Seiten verantwortlich. Die verlinkten Seiten wurden zum Zeitpunkt der
            Verlinkung auf mögliche Rechtsverstöße überprüft. Rechtswidrige Inhalte waren zum
            Zeitpunkt der Verlinkung nicht erkennbar. Eine permanente inhaltliche Kontrolle der
            verlinkten Seiten ist jedoch ohne konkrete Anhaltspunkte einer Rechtsverletzung nicht
            zumutbar. Bei Bekanntwerden von Rechtsverletzungen werden wir derartige Links umgehend
            entfernen.
          </p>
        </section>

        <section class="imp-block">
          <h2>Urheberrecht</h2>
          <p>
            Die durch die Seitenbetreiber erstellten Inhalte und Werke auf diesen Seiten unterliegen
            dem deutschen Urheberrecht. Die Vervielfältigung, Bearbeitung, Verbreitung und jede Art
            der Verwertung außerhalb der Grenzen des Urheberrechtes bedürfen der schriftlichen
            Zustimmung des jeweiligen Autors bzw. Erstellers. Downloads und Kopien dieser Seite sind
            nur für den privaten, nicht kommerziellen Gebrauch gestattet. Soweit die Inhalte auf
            dieser Seite nicht vom Betreiber erstellt wurden, werden die Urheberrechte Dritter
            beachtet. Sollten Sie trotzdem auf eine Urheberrechtsverletzung aufmerksam werden, bitten
            wir um einen entsprechenden Hinweis. Bei Bekanntwerden von Rechtsverletzungen werden wir
            derartige Inhalte umgehend entfernen.
          </p>
        </section>
      </div>
    </main>

    <footer class="imp-footer">
      <div class="imp-footer-inner">
        <p>© {{ new Date().getFullYear() }} pspixels manufactur</p>
        <nav class="imp-footer-nav">
          <a href="#datenschutz" @click.prevent="goDatenschutz">Datenschutz</a>
          <a href="/" @click.prevent="goHome">Zurück zur Startseite</a>
        </nav>
      </div>
    </footer>
  </div>
</template>

<script setup>
function goHome() {
  window.location.hash = ''
  window.scrollTo(0, 0)
}

function goDatenschutz() {
  window.location.hash = '#datenschutz'
  window.scrollTo(0, 0)
}
</script>

<style scoped>
.impressum-page {
  min-height: 100vh;
  background: var(--bg);
  display: flex;
  flex-direction: column;
}

/* Header */
.imp-header {
  background: rgba(245, 239, 228, 0.96);
  border-bottom: 1px solid var(--line);
  position: sticky;
  top: 0;
  z-index: 100;
}

.imp-header-inner {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 2rem;
  height: 68px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.imp-logo {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-style: italic;
  font-variant: small-caps;
  font-size: 1.1rem;
  font-weight: 500;
  letter-spacing: 0.04em;
  color: var(--text);
}

.imp-back {
  font-family: 'Inter', sans-serif;
  font-size: 0.75rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-muted);
  transition: color 0.2s;
}

.imp-back:hover {
  color: var(--text);
}

/* Main */
.imp-main {
  flex: 1;
  padding: 5rem 2rem;
}

.imp-inner {
  max-width: 720px;
  margin: 0 auto;
}

.imp-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 500;
  color: var(--text);
  margin-bottom: 3.5rem;
  border-bottom: 1px solid var(--line);
  padding-bottom: 1.5rem;
}

.imp-block {
  margin-bottom: 2.5rem;
  padding-bottom: 2.5rem;
  border-bottom: 1px solid var(--line);
}

.imp-block:last-child {
  border-bottom: none;
}

.imp-block h2 {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--accent-wood);
  margin-bottom: 1rem;
}

.imp-block address,
.imp-block p {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  font-weight: 300;
  color: var(--text);
  line-height: 1.8;
  font-style: normal;
}

.imp-block a {
  color: var(--primary);
  text-decoration: underline;
  text-underline-offset: 3px;
}

.imp-block a:hover {
  color: var(--primary-hover);
}

/* Footer */
.imp-footer {
  background: var(--accent-dark);
  padding: 2rem;
}

.imp-footer-inner {
  max-width: 960px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
}

.imp-footer p {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  color: #3d3028;
}

.imp-footer-nav {
  display: flex;
  gap: 1.5rem;
  align-items: center;
}

.imp-footer-nav a {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: #5a4d42;
  transition: color 0.2s;
}

.imp-footer-nav a:hover {
  color: var(--accent-light);
}

@media (max-width: 768px) {
  .imp-main {
    padding: 3rem 1.5rem;
  }

  .imp-footer-inner {
    flex-direction: column;
    text-align: center;
  }
}
</style>
