<template>
  <section class="hero">
    <!-- Background -->
    <div class="hero-bg">
      <img :src="heroImage" alt="Health Tourism Kerala" class="hero-bg-image" />
      <div class="hero-overlay"></div>

      <div class="hero-particles">
        <div
          class="particle"
          v-for="n in 20"
          :key="n"
          :style="getParticleStyle(n)"
        ></div>
      </div>
    </div>

    <div class="hero-content">
      <!-- Globe -->
      <div class="hero-visual">
        <div class="globe">
          <div class="globe-ring ring-1"></div>
          <div class="globe-ring ring-2"></div>
          <div class="globe-ring ring-3"></div>

          <div class="globe-core">
          
          </div>

          <div class="globe-glow"></div>
        </div>
      </div>

      <!-- Text -->
      <div class="hero-text">
        <span class="hero-badge">
           Premium Health Tourism
        </span>

        <h1 class="hero-title">
          Where <span class="text-coral">Healing</span><br />
          Meets <span class="text-gradient">Paradise</span>
        </h1>

        <p class="hero-subtitle">
          World-class healthcare, authentic Ayurveda, and serene destinations
          in God's Own Country — Kerala, India.
        </p>

        <div class="hero-cta">
          <a href="#packages" class="btn btn-gold">Explore Packages</a>
          <a href="#contact" class="btn btn-glass">Plan Your Journey</a>
        </div>

        <div class="hero-stats">
          <div class="stat-card">
            <span class="stat-icon">💰</span>
            <span class="stat-number">60–80%</span>
            <span class="stat-label">Lower Cost</span>
          </div>
          <div class="stat-card">
            <span class="stat-icon">🌿</span>
            <span class="stat-number">5000+</span>
            <span class="stat-label">Years Ayurveda</span>
          </div>
          <div class="stat-card">
            <span class="stat-icon">❤️</span>
            <span class="stat-number">100%</span>
            <span class="stat-label">Holistic Care</span>
          </div>
        </div>
      </div>
    </div>

    <div class="hero-scroll">
      <span>Scroll</span>
      <div class="arrow"></div>
    </div>
  </section>
</template>

<script setup>
import heroImage from '../assets/images/hero.png'

const getParticleStyle = () => ({
  left: `${Math.random() * 100}%`,
  animationDelay: `${Math.random() * 8}s`,
  animationDuration: `${14 + Math.random() * 8}s`
})
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
}

.hero-bg-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}



.hero-particles {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.particle {
  position: absolute;
  top: 100%;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255,255,255,0.6), transparent);
  animation: float linear infinite;
}

@keyframes float {
  from { transform: translateY(0); }
  to { transform: translateY(-120vh); }
}

.hero-content {
  position: relative;
  z-index: 2;
  max-width: 1400px;
  margin: auto;
  padding: 9rem 2rem 4rem;
  display: flex;
  gap: 4rem;
  align-items: center;
}

.hero-visual {
  flex-shrink: 0;
}

.globe {
  width: 260px;
  height: 260px;
  position: relative;
}

.globe-ring {
  position: absolute;
  inset: 0;
  border-radius: 50%;
  border: 2px solid rgba(31,122,107,0.3);
  animation: spin 16s linear infinite;
}

.ring-2 {
  inset: 12%;
  animation-direction: reverse;
}

.ring-3 {
  inset: 24%;
  animation-duration: 10s;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

.globe-core {
  position: absolute;
  inset: 32%;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.globe-icon {
  font-size: 3rem;
}

.globe-glow {
  position: absolute;
  inset: -10%;
  background: radial-gradient(circle, rgba(79,189,176,0.35), transparent);
}

.hero-text {
  max-width: 650px;
}

.hero-badge {
  background: rgba(255,255,255,0.7);
  padding: 0.6rem 1.4rem;
  border-radius: 999px;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  display: inline-block;
  margin-bottom: 2rem;
}

.hero-title {
  font-size: clamp(3rem, 5vw, 4.5rem);
  font-weight: 700;
  line-height: 1.1;
}

.text-coral {
  color: #00000;
}

.text-gradient {
  background: linear-gradient(120deg, #1f7a6b, #4fbdb0, #f4c97a);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-subtitle {
  margin: 1.5rem 0 2.5rem;
  color: #ffffff;
  font-size: 1.15rem;
}

.hero-cta {
  display: flex;
  gap: 1.2rem;
  margin-bottom: 3rem;
}

.btn {
  padding: 0.9rem 1.8rem;
  border-radius: 999px;
  font-weight: 600;
}

.btn-gold {
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
  color: #1c2d2a;
}

.btn-glass {
  background: rgba(255,255,255,0.75);
  backdrop-filter: blur(10px);
  color: #1f7a6b;
}

.hero-stats {
  display: grid;
  grid-template-columns: repeat(3,1fr);
  gap: 1.2rem;
}

.stat-card {
  background: rgba(255,255,255,0.75);
  border-radius: 18px;
  padding: 1.2rem;
  text-align: center;
}

.stat-number {
  font-size: 1.8rem;
  font-weight: 700;
  color: #1f7a6b;
}

.hero-scroll {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  font-size: 0.7rem;
  letter-spacing: 0.2em;
}

.arrow {
  width: 22px;
  height: 22px;
  border-right: 2px solid #1f7a6b;
  border-bottom: 2px solid #1f7a6b;
  transform: rotate(45deg);
  margin-top: 0.5rem;
}

@media (max-width: 968px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
  }
  .hero-stats {
    grid-template-columns: 1fr;
  }
}
</style>
