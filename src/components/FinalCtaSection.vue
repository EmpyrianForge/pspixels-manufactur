<template>
  <section id="kontakt" class="final-cta">
    <div class="cta-inner">

      <!-- Left: headline + direct contact -->
      <div class="cta-text reveal">
        <p class="section-label">Kontakt</p>
        <h2 class="cta-headline">
          Ihr Raum.<br />
          Ihr Ort.<br />
          Ihr Objekt.
        </h2>
        <p class="cta-sub">
          Wir fertigen auf Anfrage. Jede Anfrage wird persönlich beantwortet.
        </p>

        <div class="direct-contact">
          <p class="direct-label">Direkter Kontakt</p>
          <a href="mailto:info@pspixels-studio.de" class="direct-email">
            info@pspixels-studio.de
          </a>
          <p class="direct-note">
            Antwort in der Regel innerhalb von 48 Stunden.
          </p>
        </div>

        <div class="contact-details">
          <div class="detail-item">
            <span class="detail-key">Lieferung</span>
            <span class="detail-val">Deutschland &amp; EU</span>
          </div>
          <div class="detail-item">
            <span class="detail-key">Fertigung</span>
            <span class="detail-val">Auf Anfrage, 2–4 Wochen</span>
          </div>
          <div class="detail-item">
            <span class="detail-key">Formate</span>
            <span class="detail-val">30×30 cm bis 80×80 cm</span>
          </div>
        </div>
      </div>

      <!-- Right: form -->
      <div class="form-wrap reveal" style="transition-delay: 0.18s">
        <div v-if="!submitted" class="form-box">
          <div class="form-header">
            <h3 class="form-title">Anfrage stellen</h3>
            <p class="form-subtitle">Alle Felder mit * sind Pflichtfelder.</p>
          </div>

          <form
            id="contact-form"
            class="contact-form"
            @submit.prevent="handleSubmit"
            novalidate
          >
            <!-- Name + Type row -->
            <div class="form-row">
              <div class="form-group" :class="{ 'has-error': errors.name }">
                <label for="name">Name *</label>
                <input
                  id="name"
                  v-model="form.name"
                  type="text"
                  placeholder="Ihr vollständiger Name"
                  autocomplete="name"
                  @blur="validateField('name')"
                />
                <span v-if="errors.name" class="error-msg">{{ errors.name }}</span>
              </div>

              <div class="form-group">
                <label for="type">Anfragetyp</label>
                <div class="select-wrap">
                  <select id="type" v-model="form.type">
                    <option value="">Bitte wählen …</option>
                    <option value="Projekt anfragen">Projekt anfragen</option>
                    <option value="Beratung anfordern">Beratung anfordern</option>
                    <option value="Katalog anfragen">Katalog anfragen</option>
                    <option value="Materialmuster anfordern">Materialmuster anfordern</option>
                    <option value="B2B / Großbestellung">B2B / Großbestellung</option>
                    <option value="Sonstiges">Sonstiges</option>
                  </select>
                  <span class="select-arrow" aria-hidden="true">↓</span>
                </div>
              </div>
            </div>

            <!-- Email + Phone row -->
            <div class="form-row">
              <div class="form-group" :class="{ 'has-error': errors.email }">
                <label for="email">E-Mail *</label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  placeholder="ihre@email.de"
                  autocomplete="email"
                  @blur="validateField('email')"
                />
                <span v-if="errors.email" class="error-msg">{{ errors.email }}</span>
              </div>

              <div class="form-group">
                <label for="phone">Telefon <span class="optional">(optional)</span></label>
                <input
                  id="phone"
                  v-model="form.phone"
                  type="tel"
                  placeholder="+49 …"
                  autocomplete="tel"
                />
              </div>
            </div>

            <!-- Location -->
            <div class="form-group">
              <label for="location">Ort / Region <span class="optional">(optional)</span></label>
              <input
                id="location"
                v-model="form.location"
                type="text"
                placeholder="z. B. Mallorca, Allgäu, Nordseeküste …"
              />
            </div>

            <!-- Message -->
            <div class="form-group" :class="{ 'has-error': errors.message }">
              <label for="message">Nachricht *</label>
              <textarea
                id="message"
                v-model="form.message"
                rows="5"
                placeholder="Beschreiben Sie Ihr Vorhaben — gewünschter Ort, Format, Holzart, Menge …"
                @blur="validateField('message')"
              ></textarea>
              <span v-if="errors.message" class="error-msg">{{ errors.message }}</span>
            </div>

            <!-- Privacy -->
            <div class="form-group form-privacy">
              <label class="checkbox-label">
                <input type="checkbox" v-model="form.privacy" />
                <span>
                  Ich habe die
                  <a href="#datenschutz" @click.prevent="goDataschutz">Datenschutzerklärung</a>
                  gelesen und bin einverstanden. *
                </span>
              </label>
              <span v-if="errors.privacy" class="error-msg">{{ errors.privacy }}</span>
            </div>

            <button
              type="submit"
              class="btn-submit"
              :class="{ 'is-loading': loading }"
              :disabled="loading"
            >
              <span v-if="!loading">Anfrage absenden</span>
              <span v-else class="loading-dots">Wird gesendet<span>.</span><span>.</span><span>.</span></span>
            </button>

            <p v-if="sendError" class="send-error">
              Beim Senden ist ein Fehler aufgetreten. Bitte schreiben Sie uns direkt an
              <a href="mailto:info@pspixels-studio.de">info@pspixels-studio.de</a>
            </p>
          </form>
        </div>

        <!-- Success state -->
        <div v-else class="form-success">
          <div class="success-icon" aria-hidden="true">✓</div>
          <h3 class="success-title">Anfrage erhalten.</h3>
          <p class="success-body">
            Vielen Dank für Ihre Nachricht. Wir melden uns persönlich
            innerhalb von 48 Stunden.
          </p>
          <a href="mailto:info@pspixels-studio.de" class="success-email">
            info@pspixels-studio.de
          </a>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'

const FORMSPREE_ENDPOINT = 'https://formsubmit.co/ajax/info@pspixels-studio.de'

const submitted = ref(false)
const loading = ref(false)
const sendError = ref(false)

const form = reactive({
  name: '',
  email: '',
  phone: '',
  location: '',
  type: '',
  message: '',
  privacy: false,
})

const errors = reactive({
  name: '',
  email: '',
  message: '',
  privacy: '',
})

function validateField(field) {
  if (field === 'name') {
    errors.name = form.name.trim() ? '' : 'Bitte geben Sie Ihren Namen an.'
  }
  if (field === 'email') {
    if (!form.email.trim()) {
      errors.email = 'Bitte geben Sie Ihre E-Mail-Adresse an.'
    } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)) {
      errors.email = 'Bitte geben Sie eine gültige E-Mail-Adresse an.'
    } else {
      errors.email = ''
    }
  }
  if (field === 'message') {
    errors.message = form.message.trim() ? '' : 'Bitte schreiben Sie eine kurze Nachricht.'
  }
}

function validateAll() {
  validateField('name')
  validateField('email')
  validateField('message')
  errors.privacy = form.privacy ? '' : 'Bitte stimmen Sie der Datenschutzerklärung zu.'
  return !errors.name && !errors.email && !errors.message && !errors.privacy
}

async function handleSubmit() {
  if (!validateAll()) return

  loading.value = true
  sendError.value = false

  try {
    const res = await fetch(FORMSPREE_ENDPOINT, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json', Accept: 'application/json' },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        phone: form.phone || '—',
        location: form.location || '—',
        type: form.type || '—',
        message: form.message,
        _replyto: form.email,
        _subject: `Anfrage von ${form.name}${form.type ? ' — ' + form.type : ''}`,
      }),
    })

    if (res.ok) {
      submitted.value = true
    } else {
      sendError.value = true
    }
  } catch {
    sendError.value = true
  } finally {
    loading.value = false
  }
}

function goDataschutz() {
  window.location.hash = '#datenschutz'
  window.scrollTo(0, 0)
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
  grid-template-columns: 1fr 1.4fr;
  gap: 7rem;
  align-items: start;
}

/* ── Left column ── */
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
  font-size: clamp(3rem, 5vw, 4.5rem);
  font-weight: 500;
  line-height: 1.05;
  color: var(--white);
  margin-bottom: 1.25rem;
}

.cta-sub {
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  color: #8a7a6a;
  line-height: 1.7;
  margin-bottom: 3rem;
}

.direct-contact {
  margin-bottom: 3rem;
  padding: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.07);
  background: rgba(255, 255, 255, 0.03);
}

.direct-label {
  font-family: 'Inter', sans-serif;
  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--accent-light);
  opacity: 0.6;
  margin-bottom: 0.75rem;
}

.direct-email {
  display: block;
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.3rem;
  font-style: italic;
  color: var(--accent-light);
  margin-bottom: 0.75rem;
  transition: opacity 0.2s;
}

.direct-email:hover {
  opacity: 0.75;
}

.direct-note {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 300;
  color: #5a4d42;
}

.contact-details {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.detail-item {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  gap: 1rem;
}

.detail-key {
  font-family: 'Inter', sans-serif;
  font-size: 0.68rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #5a4d42;
}

.detail-val {
  font-family: 'Inter', sans-serif;
  font-size: 0.82rem;
  font-weight: 300;
  color: #8a7a6a;
  text-align: right;
}

/* ── Form box ── */
.form-wrap {
  position: relative;
}

.form-box {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 3rem;
}

.form-header {
  margin-bottom: 2.5rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.07);
}

.form-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.75rem;
  font-weight: 500;
  color: var(--white);
  margin-bottom: 0.4rem;
}

.form-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 300;
  color: #5a4d42;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.25rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  font-family: 'Inter', sans-serif;
  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #6a5a4a;
}

.optional {
  font-weight: 300;
  text-transform: none;
  letter-spacing: 0;
  font-size: 0.65rem;
  color: #4a3f35;
}

.form-group input,
.form-group textarea {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.08);
  color: var(--white);
  padding: 0.9rem 1rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  outline: none;
  transition: border-color 0.2s, background 0.2s;
  resize: vertical;
  width: 100%;
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: #4a3f35;
}

.form-group input:focus,
.form-group textarea:focus {
  border-color: rgba(201, 168, 124, 0.4);
  background: rgba(255, 255, 255, 0.07);
}

.has-error input,
.has-error textarea {
  border-color: rgba(180, 80, 60, 0.5);
}

.error-msg {
  font-family: 'Inter', sans-serif;
  font-size: 0.68rem;
  color: #c47a6a;
  font-weight: 300;
}

/* Select */
.select-wrap {
  position: relative;
}

.select-wrap select {
  width: 100%;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.08);
  color: var(--white);
  padding: 0.9rem 2.5rem 0.9rem 1rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  outline: none;
  appearance: none;
  cursor: pointer;
  transition: border-color 0.2s;
}

.select-wrap select:focus {
  border-color: rgba(201, 168, 124, 0.4);
}

.select-wrap select option {
  background: #2a1c10;
  color: var(--white);
}

.select-arrow {
  position: absolute;
  right: 1rem;
  top: 50%;
  transform: translateY(-50%);
  color: #5a4d42;
  font-size: 0.75rem;
  pointer-events: none;
}

/* Checkbox / privacy */
.form-privacy {
  gap: 0.4rem;
}

.checkbox-label {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  cursor: pointer;
}

.checkbox-label input[type="checkbox"] {
  width: 16px;
  height: 16px;
  min-width: 16px;
  margin-top: 2px;
  accent-color: var(--primary);
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.15);
  cursor: pointer;
  padding: 0;
}

.checkbox-label span {
  font-family: 'Inter', sans-serif;
  font-size: 0.78rem;
  font-weight: 300;
  color: #6a5a4a;
  line-height: 1.6;
}

.checkbox-label a {
  color: var(--accent-light);
  text-decoration: underline;
  text-underline-offset: 2px;
  opacity: 0.8;
}

.checkbox-label a:hover {
  opacity: 1;
}

/* Submit */
.btn-submit {
  background: var(--primary);
  color: var(--white);
  border: none;
  padding: 1.1rem 2rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  cursor: pointer;
  transition: background 0.2s;
  width: 100%;
  margin-top: 0.5rem;
}

.btn-submit:hover:not(:disabled) {
  background: var(--primary-hover);
}

.btn-submit:disabled {
  opacity: 0.6;
  cursor: default;
}

/* Loading dots animation */
.loading-dots span {
  animation: blink 1.2s infinite;
}
.loading-dots span:nth-child(2) { animation-delay: 0.2s; }
.loading-dots span:nth-child(3) { animation-delay: 0.4s; }

@keyframes blink {
  0%, 80%, 100% { opacity: 0; }
  40% { opacity: 1; }
}

.send-error {
  font-family: 'Inter', sans-serif;
  font-size: 0.78rem;
  font-weight: 300;
  color: #c47a6a;
  line-height: 1.6;
  text-align: center;
  margin-top: 0.5rem;
}

.send-error a {
  color: var(--accent-light);
  text-decoration: underline;
  text-underline-offset: 2px;
}

/* Success state */
.form-success {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.08);
  padding: 4rem 3rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 1rem;
}

.success-icon {
  width: 48px;
  height: 48px;
  border: 1px solid var(--primary);
  color: var(--primary);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

.success-title {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 2rem;
  font-weight: 500;
  color: var(--white);
}

.success-body {
  font-family: 'Inter', sans-serif;
  font-size: 0.875rem;
  font-weight: 300;
  color: #8a7a6a;
  line-height: 1.7;
  max-width: 38ch;
}

.success-email {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.1rem;
  font-style: italic;
  color: var(--accent-light);
  margin-top: 0.5rem;
  transition: opacity 0.2s;
}

.success-email:hover {
  opacity: 0.75;
}

/* Responsive */
@media (max-width: 1100px) {
  .cta-inner {
    grid-template-columns: 1fr;
    gap: 4rem;
  }
}

@media (max-width: 768px) {
  .final-cta {
    padding: 5rem 1.5rem;
  }

  .form-box {
    padding: 2rem 1.5rem;
  }

  .form-row {
    grid-template-columns: 1fr;
  }
}
</style>
