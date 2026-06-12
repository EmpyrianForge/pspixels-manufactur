<template>
  <section class="hero" aria-label="Hero">
    <div class="hero-inner">
      <div class="hero-text" :class="{ 'fade-in': loaded }">
        <p class="hero-eyebrow">Topografische Reliefkarten aus Holz &amp; 3D-Druck</p>
        <h1 class="hero-headline">
          Wo echtes Holz auf<br />
          präzisen 3D-Druck trifft.
        </h1>
        <p class="hero-subline">
          Für Hotels, Ferienhäuser und besondere Räume.<br />
          Handgefertigt, materialstark und auf Wunsch mit individueller Gravur.
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
          <div class="canvas-wrap" ref="canvasWrap">
            <canvas ref="canvas" class="model-canvas"></canvas>
          </div>
          <div class="product-label">
            <span class="label-place">Mallorca</span>
            <span class="label-sub">Topografisches Relief – Echtholz – PLA</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import * as THREE from 'three'
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js'
import { OrbitControls } from 'three/addons/controls/OrbitControls.js'

const loaded = ref(false)
const canvas = ref(null)
const canvasWrap = ref(null)

let renderer, scene, camera, controls, pivot, animId

const DEG80 = Math.PI * 80 / 180
const mouse = { x: 0, y: 0 }
const current = { x: 0, y: 0 }

function onMouseMove(e) {
  mouse.x = (e.clientX / window.innerWidth) * 2 - 1
  mouse.y = -((e.clientY / window.innerHeight) * 2 - 1)
}

function initThree() {
  const wrap = canvasWrap.value
  const w = wrap.clientWidth
  const h = wrap.clientHeight

  renderer = new THREE.WebGLRenderer({ canvas: canvas.value, antialias: true, alpha: true })
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))
  renderer.setSize(w, h)
  renderer.outputColorSpace = THREE.SRGBColorSpace
  renderer.shadowMap.enabled = true
  renderer.shadowMap.type = THREE.PCFSoftShadowMap

  scene = new THREE.Scene()

  camera = new THREE.PerspectiveCamera(38, w / h, 0.01, 100)
  camera.position.set(0, 0, 2.4)

  // orbit controls — drag to rotate, clamped to ±80°
  controls = new OrbitControls(camera, canvas.value)
  controls.enableZoom = false
  controls.enablePan = false
  controls.minAzimuthAngle = -DEG80
  controls.maxAzimuthAngle = DEG80
  controls.minPolarAngle = Math.PI / 2 - DEG80
  controls.maxPolarAngle = Math.PI / 2 + DEG80
  controls.enableDamping = true
  controls.dampingFactor = 0.07

  // lights
  const ambient = new THREE.AmbientLight(0xfff5e8, 1.6)
  scene.add(ambient)

  const key = new THREE.DirectionalLight(0xfff8f0, 3.5)
  key.position.set(2, 4, 3)
  key.castShadow = true
  scene.add(key)

  const fill = new THREE.DirectionalLight(0xe8f0ff, 1.2)
  fill.position.set(-3, 1, 2)
  scene.add(fill)

  const rim = new THREE.DirectionalLight(0xffddb0, 0.8)
  rim.position.set(0, -2, -3)
  scene.add(rim)

  const loader = new GLTFLoader()
  loader.load('/Modell/Map-Werbung.glb', (gltf) => {
    const model = gltf.scene

    const box = new THREE.Box3().setFromObject(model)
    const size = box.getSize(new THREE.Vector3())
    const maxDim = Math.max(size.x, size.y, size.z)
    model.scale.setScalar(1.4 / maxDim)

    const box2 = new THREE.Box3().setFromObject(model)
    const centre = box2.getCenter(new THREE.Vector3())
    model.position.sub(centre)

    model.traverse((child) => {
      if (child.isMesh) {
        child.castShadow = true
        child.receiveShadow = true
      }
    })

    pivot = new THREE.Group()
    pivot.add(model)
    scene.add(pivot)
  })

  animate()
}

function animate() {
  animId = requestAnimationFrame(animate)

  // smooth mouse-follow on the pivot (subtle tilt, ±5°)
  current.x += (mouse.x - current.x) * 0.05
  current.y += (mouse.y - current.y) * 0.05
  if (pivot) {
    pivot.rotation.y = current.x * 0.18
    pivot.rotation.x = -current.y * 0.12
  }

  controls.update()
  renderer.render(scene, camera)
}

function onResize() {
  if (!canvasWrap.value) return
  const w = canvasWrap.value.clientWidth
  const h = canvasWrap.value.clientHeight
  camera.aspect = w / h
  camera.updateProjectionMatrix()
  renderer.setSize(w, h)
}

onMounted(() => {
  requestAnimationFrame(() => {
    setTimeout(() => { loaded.value = true }, 80)
  })
  initThree()
  window.addEventListener('mousemove', onMouseMove)
  window.addEventListener('resize', onResize)
})

onBeforeUnmount(() => {
  cancelAnimationFrame(animId)
  controls?.dispose()
  renderer?.dispose()
  window.removeEventListener('mousemove', onMouseMove)
  window.removeEventListener('resize', onResize)
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
  width: 100%;
}

.canvas-wrap {
  width: 480px;
  height: 560px;
  position: relative;
  cursor: grab;
}

.canvas-wrap:active {
  cursor: grabbing;
}

.model-canvas {
  width: 100%;
  height: 100%;
  display: block;
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

  .canvas-wrap {
    width: 320px;
    height: 380px;
  }
}
</style>
