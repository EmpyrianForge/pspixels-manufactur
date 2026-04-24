<template>
  <section class="hero" aria-label="Hero">
    <div class="hero-inner">
      <div class="hero-text" :class="{ 'fade-in': loaded }">
        <p class="hero-eyebrow">Wandobjekte aus Holz &amp; 3D-Druck</p>
        <h1 class="hero-headline">
          Wo echtes Holz auf<br />
          präzisen 3D-Druck trifft.
        </h1>
        <p class="hero-subline">
          Topografische Reliefkarten für Räume,<br />
          die Materialität spürbar machen.
        </p>
        <div class="hero-ctas">
          <a href="#kontakt" class="btn-primary">Projekt anfragen</a>
          <a href="#referenzen" class="btn-ghost">Kollektion entdecken</a>
        </div>
        <p class="trust-badge">
          <span>Echtes Holz</span>
          <span class="dot">·</span>
          <span>Präziser 3D-Druck</span>
          <span class="dot">·</span>
          <span>Handgefertigt</span>
        </p>
      </div>

      <div class="hero-visual" :class="{ 'fade-in-right': loaded }" aria-hidden="true">
        <div class="product-frame">
          <svg
            viewBox="0 0 320 420"
            xmlns="http://www.w3.org/2000/svg"
            class="product-svg"
          >
            <!-- Wood board background -->
            <defs>
              <linearGradient id="woodGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                <stop offset="0%" style="stop-color:#3d2b1a;stop-opacity:1" />
                <stop offset="40%" style="stop-color:#4a3320;stop-opacity:1" />
                <stop offset="100%" style="stop-color:#2c1e10;stop-opacity:1" />
              </linearGradient>
              <!-- Wood grain lines -->
              <pattern id="grain" patternUnits="userSpaceOnUse" width="320" height="420">
                <line x1="0" y1="60" x2="320" y2="55" stroke="#5a3d22" stroke-width="0.5" opacity="0.4"/>
                <line x1="0" y1="110" x2="320" y2="108" stroke="#5a3d22" stroke-width="0.3" opacity="0.3"/>
                <line x1="0" y1="160" x2="320" y2="163" stroke="#5a3d22" stroke-width="0.4" opacity="0.35"/>
                <line x1="0" y1="220" x2="320" y2="217" stroke="#5a3d22" stroke-width="0.3" opacity="0.3"/>
                <line x1="0" y1="280" x2="320" y2="282" stroke="#5a3d22" stroke-width="0.4" opacity="0.3"/>
                <line x1="0" y1="340" x2="320" y2="338" stroke="#5a3d22" stroke-width="0.3" opacity="0.25"/>
              </pattern>
              <filter id="reliefShadow">
                <feDropShadow dx="0" dy="3" stdDeviation="4" flood-color="#1a0e06" flood-opacity="0.5"/>
              </filter>
              <filter id="subtleGlow">
                <feDropShadow dx="0" dy="1" stdDeviation="2" flood-color="#e8e0d5" flood-opacity="0.3"/>
              </filter>
            </defs>

            <!-- Board -->
            <rect x="10" y="10" width="300" height="400" rx="3" fill="url(#woodGrad)" />
            <rect x="10" y="10" width="300" height="400" rx="3" fill="url(#grain)" />

            <!-- Board edge highlight (top) -->
            <rect x="10" y="10" width="300" height="2" rx="1" fill="#6b4a28" opacity="0.6"/>
            <!-- Board edge shadow (bottom) -->
            <rect x="10" y="408" width="300" height="2" rx="1" fill="#1a0e06" opacity="0.8"/>

            <!-- Mallorca-like topographic relief — organic island silhouette -->
            <!-- Outer island shape (lowest relief layer) -->
            <path
              d="M 90 290
                 C 70 285, 55 270, 52 255
                 C 48 238, 55 218, 60 205
                 C 65 190, 62 175, 68 162
                 C 74 148, 82 138, 92 130
                 C 102 122, 115 118, 128 115
                 C 142 112, 155 110, 168 112
                 C 182 114, 194 120, 205 128
                 C 218 136, 228 148, 235 160
                 C 243 174, 248 190, 248 206
                 C 248 222, 244 238, 238 250
                 C 230 266, 216 278, 200 286
                 C 184 294, 165 298, 148 298
                 C 130 298, 108 296, 90 290 Z"
              fill="#c8bfb0"
              filter="url(#reliefShadow)"
            />

            <!-- Mid relief layer -->
            <path
              d="M 105 272
                 C 90 266, 80 252, 78 238
                 C 76 222, 82 206, 88 194
                 C 94 180, 96 166, 104 155
                 C 112 144, 124 136, 136 132
                 C 150 128, 162 128, 175 132
                 C 188 136, 200 146, 208 158
                 C 216 170, 220 186, 218 200
                 C 216 216, 210 230, 200 240
                 C 190 252, 176 260, 160 264
                 C 144 268, 122 278, 105 272 Z"
              fill="#dbd4c8"
              filter="url(#subtleGlow)"
            />

            <!-- Inner relief — highlands -->
            <path
              d="M 126 248
                 C 114 242, 108 230, 108 218
                 C 108 204, 114 192, 122 182
                 C 130 172, 140 165, 152 163
                 C 164 161, 176 164, 186 172
                 C 196 180, 202 194, 200 206
                 C 198 220, 190 232, 178 240
                 C 166 248, 150 254, 136 252
                 C 132 251, 128 250, 126 248 Z"
              fill="#ede8e0"
            />

            <!-- Peak / summit -->
            <path
              d="M 148 224
                 C 144 218, 142 210, 144 202
                 C 146 194, 152 188, 158 186
                 C 165 184, 172 188, 174 196
                 C 177 204, 174 214, 168 220
                 C 162 226, 154 228, 148 224 Z"
              fill="#f5f2ee"
            />

            <!-- Small northern peninsula -->
            <path
              d="M 185 128 C 190 118, 198 110, 208 108 C 216 106, 224 110, 226 118 C 228 126, 222 134, 212 136 C 204 138, 194 136, 185 128 Z"
              fill="#c8bfb0"
            />
            <path
              d="M 190 126 C 194 118, 202 114, 210 116 C 218 118, 220 126, 214 132 C 208 136, 198 134, 190 126 Z"
              fill="#dbd4c8"
            />

            <!-- Contour lines on the main relief -->
            <path
              d="M 115 258 C 100 250, 92 236, 92 222 C 92 206, 100 192, 110 182"
              fill="none" stroke="#b8b0a4" stroke-width="0.6" opacity="0.5"/>
            <path
              d="M 205 258 C 218 248, 224 232, 222 216 C 220 198, 212 184, 200 174"
              fill="none" stroke="#b8b0a4" stroke-width="0.6" opacity="0.5"/>
            <path
              d="M 130 168 C 142 162, 156 160, 168 164 C 180 168, 190 176, 196 186"
              fill="none" stroke="#b8b0a4" stroke-width="0.6" opacity="0.5"/>

            <!-- Brand text on board -->
            <text x="160" y="356" text-anchor="middle" font-family="Georgia, serif" font-size="9" fill="#8a6a45" letter-spacing="3" opacity="0.7">PSPIXELS MANUFACTUR</text>
            <line x1="80" y1="362" x2="240" y2="362" stroke="#6b4a28" stroke-width="0.5" opacity="0.4"/>

            <!-- Hanging mount holes -->
            <circle cx="60" cy="35" r="4" fill="#2c1e10" stroke="#1a0e06" stroke-width="1"/>
            <circle cx="260" cy="35" r="4" fill="#2c1e10" stroke="#1a0e06" stroke-width="1"/>
          </svg>

          <div class="product-label">
            <span class="label-place">Mallorca</span>
            <span class="label-sub">Topografisches Relief · Walnuss + PLA</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const loaded = ref(false)
onMounted(() => {
  requestAnimationFrame(() => {
    setTimeout(() => { loaded.value = true }, 80)
  })
})
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  background-color: var(--bg);
  padding-top: 68px;
  overflow: hidden;
}

.hero-inner {
  max-width: 1280px;
  margin: 0 auto;
  padding: 4rem 2rem;
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: 5rem;
  width: 100%;
}

/* Fade-in animations */
.hero-text {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.hero-text.fade-in {
  opacity: 1;
  transform: none;
}

.hero-visual {
  opacity: 0;
  transform: translateX(30px);
  transition: opacity 0.9s ease 0.2s, transform 0.9s ease 0.2s;
  display: flex;
  justify-content: center;
}
.hero-visual.fade-in-right {
  opacity: 1;
  transform: none;
}

/* Text */
.hero-eyebrow {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  font-weight: 400;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--accent-wood);
  margin-bottom: 1.5rem;
}

.hero-headline {
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: clamp(3rem, 6vw, 5.5rem);
  font-weight: 500;
  line-height: 1.08;
  color: var(--text);
  margin-bottom: 1.5rem;
}

.hero-subline {
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  font-weight: 300;
  color: var(--text-muted);
  line-height: 1.7;
  margin-bottom: 2.5rem;
}

.hero-ctas {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin-bottom: 2.5rem;
}

.btn-primary {
  display: inline-block;
  background: var(--primary);
  color: var(--white);
  padding: 0.85rem 2rem;
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

.btn-ghost {
  display: inline-block;
  border: 1px solid var(--line);
  color: var(--text-muted);
  padding: 0.85rem 2rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  transition: border-color 0.2s, color 0.2s;
}

.btn-ghost:hover {
  border-color: var(--text-muted);
  color: var(--text);
}

.trust-badge {
  font-family: 'Inter', sans-serif;
  font-size: 0.72rem;
  color: var(--text-muted);
  letter-spacing: 0.06em;
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.trust-badge .dot {
  color: var(--accent-light);
}

/* Product visual */
.product-frame {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.product-svg {
  width: 280px;
  height: auto;
  filter: drop-shadow(0 20px 60px rgba(30, 20, 10, 0.35)) drop-shadow(0 4px 16px rgba(30, 20, 10, 0.2));
}

.product-label {
  text-align: center;
}

.label-place {
  display: block;
  font-family: 'Cormorant Garamond', Georgia, serif;
  font-size: 1.4rem;
  font-style: italic;
  color: var(--text);
  margin-bottom: 0.25rem;
}

.label-sub {
  display: block;
  font-family: 'Inter', sans-serif;
  font-size: 0.68rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--text-muted);
}

@media (max-width: 768px) {
  .hero-inner {
    grid-template-columns: 1fr;
    gap: 3rem;
    padding: 3rem 1.5rem;
    text-align: center;
  }

  .hero-ctas {
    justify-content: center;
  }

  .trust-badge {
    justify-content: center;
  }

  .hero-visual {
    order: -1;
  }

  .product-svg {
    width: 200px;
  }
}
</style>
