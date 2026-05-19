<template>
  <main>
    <!-- Canvas fijo -->
    <div class="fixed-canvas">
      <ClientOnly>
        <TresCanvas window-size clear-color="#111111">

          <TresPerspectiveCamera :position="[0, 0, 8]" />
          <OrbitControls />

          <!-- Escena 3D -->
          <MorphScene />

          <!-- Luces mejoradas -->
          <TresAmbientLight :intensity="0.8" />
          <TresDirectionalLight :position="[3, 5, 5]" :intensity="1.2" />

        </TresCanvas>

        <template #fallback>
          <div class="loader">Cargando modelos 3D...</div>
        </template>

      </ClientOnly>
    </div>

    <!-- Scroll -->
    <div id="scroll-wrapper">
      <section v-for="n in 5" :key="n" class="step-section">
        <div class="content-card">
          <span class="step">STEP 0{{ n }}</span>
          <h2>Desintegración Figurativa</h2>
          <p>
            Transformación progresiva del modelo 3D en partículas mediante morphing y scroll interactivo.
          </p>

          <div class="line"></div>
        </div>
      </section>
    </div>
  </main>
</template>

<style scoped>
.fixed-canvas {
  position: fixed;
  inset: 0;
  z-index: 0;
}

#scroll-wrapper {
  height: 800vh;
  position: relative;
  z-index: 10;
}

/* 🔥 Sección tipo full screen */
.step-section {
  height: 100vh;
  display: flex;
  align-items: center;
  padding-left: 8%;

  opacity: 0.4;
  transform: translateY(40px);
  transition: all 0.6s ease;
}

/* hover suave */
.step-section:hover {
  opacity: 1;
  transform: translateY(0);
}

/* 💳 CARD moderna */
.content-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(18px);

  padding: 2rem;
  border-radius: 18px;

  border: 1px solid rgba(255, 255, 255, 0.12);

  color: white;
  max-width: 420px;

  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
}

/* STEP label */
.step {
  font-size: 0.75rem;
  letter-spacing: 4px;
  opacity: 0.6;
  display: block;
  margin-bottom: 10px;
}

/* título */
.content-card h2 {
  font-size: 1.6rem;
  margin-bottom: 10px;
}

/* texto */
.content-card p {
  font-size: 0.95rem;
  opacity: 0.75;
  line-height: 1.5;
}

/* línea decorativa */
.line {
  margin-top: 20px;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, #00f3ff, transparent);
}

/* loader */
.loader {
  color: #00f3ff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: monospace;
}
</style>