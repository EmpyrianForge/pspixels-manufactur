<template>
  <footer class="site-footer">
    <div class="footer-inner">
      <div class="footer-brand">
        <p class="brand-name">Pspixels Studio</p>
        <p class="brand-tagline">Topografische Reliefkarten aus Holz &amp; 3D-Druck. — pspixels-studio.de</p>
      </div>

      <nav class="footer-nav" aria-label="Footernavigation">
        <a href="#materialien">Materialien</a>
        <a href="#fertigung">Fertigung</a>
        <a href="#referenzen">Referenzen</a>
        <a href="#kontakt">Kontakt</a>
        <a href="#impressum" class="footer-legal">Impressum</a>
        <a href="#datenschutz" class="footer-legal">Datenschutz</a>
      </nav>

      <p class="footer-copy">© {{ new Date().getFullYear() }} Pspixels Studio</p>
    </div>
  </footer>
</template>

<script setup>
</script>

<style scoped>
.site-footer {
  background: var(--accent-dark);
  border-top: 1px solid rgba(255, 255, 255, 0.06);
  padding: 3rem 2rem;
}

.footer-inner {
  max-width: 1280px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
  gap: 2rem;
}

.footer-brand {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.brand-name {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-style: italic;
  font-variant: small-caps;
  font-size: 1rem;
  color: var(--accent-light);
  letter-spacing: 0.04em;
}

.brand-tagline {
  font-family: 'Inter', sans-serif;
  font-size: 0.7rem;
  font-weight: 300;
  color: #5a4d42;
}

.footer-nav {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.footer-nav a {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #5a4d42;
  transition: color 0.2s;
}

.footer-nav a:hover {
  color: var(--accent-light);
}

.footer-copy {
  font-family: 'Inter', sans-serif;
  font-size: 0.68rem;
  color: #3d3028;
  text-align: right;
}

.footer-legal {
  opacity: 0.6;
  border-left: 1px solid #3d3028;
  padding-left: 2rem;
}

@media (max-width: 768px) {
  .footer-inner {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 1.5rem;
  }

  .footer-brand {
    align-items: center;
  }

  .footer-nav {
    justify-content: center;
    flex-wrap: wrap;
    gap: 1.25rem;
  }

  .footer-copy {
    text-align: center;
  }
}
</style>
