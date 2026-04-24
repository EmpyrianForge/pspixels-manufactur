<template>
  <section id="kontakt" class="final-cta">
    <div class="cta-inner">
      <div class="cta-text reveal">
        <p class="section-label">Kontakt</p>
        <h2 class="cta-headline">
          Ihr Raum.<br />
          Ihr Ort.<br />
          Ihr Objekt.
        </h2>
        <p class="cta-sub">Wir fertigen auf Anfrage. Keine Massenware.</p>

        <div class="cta-buttons">
          <a href="#contact-form" class="btn-primary">Projekt anfragen</a>
          <a href="#contact-form" class="btn-ghost-light">Materialmuster anfordern</a>
        </div>
      </div>

      <div class="contact-form-wrap reveal" style="transition-delay: 0.15s">
        <form id="contact-form" class="contact-form" @submit.prevent="handleSubmit" novalidate>
          <h3 class="form-title">Anfrage stellen</h3>

          <div class="form-group">
            <label for="name">Name</label>
            <input
              id="name"
              v-model="form.name"
              type="text"
              placeholder="Ihr Name"
              autocomplete="name"
              required
            />
          </div>

          <div class="form-group">
            <label for="email">E-Mail</label>
            <input
              id="email"
              v-model="form.email"
              type="email"
              placeholder="ihre@email.de"
              autocomplete="email"
              required
            />
          </div>

          <div class="form-group">
            <label for="message">Nachricht</label>
            <textarea
              id="message"
              v-model="form.message"
              rows="5"
              placeholder="Ihr Projekt, Ihr Ort, Ihre Vorstellung …"
              required
            ></textarea>
          </div>

          <button type="submit" class="btn-submit" :disabled="submitted">
            <span v-if="!submitted">Anfrage senden</span>
            <span v-else>Gesendet — wir melden uns.</span>
          </button>

          <p class="form-note">
            Kein Formular für die Ablage. Jede Anfrage wird persönlich beantwortet.
          </p>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

const submitted = ref(false)
const form = reactive({
  name: '',
  email: '',
  message: '',
})

function handleSubmit() {
  if (!form.name || !form.email || !form.message) return
  // Frontend-only: just show success state
  submitted.value = true
}
</script>

<style scoped>
.final-cta {
  background: var(--accent-dark);
  padding: 8rem 2rem;
}

.cta-inner {
  max-width: 1280px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: start;
}

.section-label {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--accent-light);
  opacity: 0.7;
  margin-bottom: 1.5rem;
}

.cta-headline {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(3rem, 5.5vw, 5rem);
  font-weight: 500;
  line-height: 1.05;
  color: var(--white);
  margin-bottom: 1.5rem;
}

.cta-sub {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  font-weight: 300;
  color: #a08a6e;
  margin-bottom: 2.5rem;
  line-height: 1.6;
}

.cta-buttons {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1rem;
}

.btn-primary {
  display: inline-block;
  background: var(--primary);
  color: var(--white);
  padding: 0.9rem 2.2rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  transition: background 0.2s;
}

.btn-primary:hover {
  background: var(--primary-hover);
}

.btn-ghost-light {
  display: inline-block;
  border: 1px solid #4a3f35;
  color: #a08a6e;
  padding: 0.9rem 2.2rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  transition: border-color 0.2s, color 0.2s;
}

.btn-ghost-light:hover {
  border-color: #7a6555;
  color: var(--accent-light);
}

/* Form */
.contact-form-wrap {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.07);
  padding: 3rem;
}

.form-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.5rem;
  font-weight: 500;
  color: var(--white);
  margin-bottom: 2rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #7a6a5a;
}

.form-group input,
.form-group textarea {
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: var(--white);
  padding: 0.85rem 1rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  outline: none;
  transition: border-color 0.2s;
  resize: vertical;
  width: 100%;
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: #5a4d42;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: rgba(255, 255, 255, 0.25);
}

.btn-submit {
  background: var(--primary);
  color: var(--white);
  border: none;
  padding: 1rem 2rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  cursor: pointer;
  transition: background 0.2s;
  width: 100%;
}

.btn-submit:hover:not(:disabled) {
  background: var(--primary-hover);
}

.btn-submit:disabled {
  background: #3a5138;
  cursor: default;
  opacity: 0.7;
}

.form-note {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 300;
  color: #5a4d42;
  text-align: center;
  line-height: 1.6;
}

@media (max-width: 1024px) {
  .cta-inner {
    grid-template-columns: 1fr;
    gap: 4rem;
  }
}

@media (max-width: 768px) {
  .final-cta {
    padding: 5rem 1.5rem;
  }

  .contact-form-wrap {
    padding: 2rem 1.5rem;
  }

  .cta-buttons {
    align-items: stretch;
  }

  .btn-primary,
  .btn-ghost-light {
    text-align: center;
  }
}
</style>
