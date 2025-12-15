<template>
  <section id="why-kerala" class="section section-dark bg-section">
    <!-- Background overlay -->
    <div class="bg-overlay"></div>

    <div class="container content-wrapper">
      <!-- Header -->
      <div class="section-header">
        <span class="subtitle">Why Choose Us</span>
        <h2>Discover <span class="text-gradient">Kerala</span></h2>
        <p class="text-muted">
          God's Own Country - Where world-class healthcare meets ancient healing traditions
        </p>
      </div>

      <!-- Features -->
      <div class="features-grid">
        <div
          v-for="(feature, index) in features"
          :key="index"
          class="feature-card glass-card"
        >
          <div class="feature-icon">{{ feature.icon }}</div>
          <h3 class="feature-title">{{ feature.title }}</h3>
          <p class="feature-desc">{{ feature.description }}</p>
        </div>
      </div>

      <!-- Ayurveda Highlight -->
      <div class="ayurveda-highlight">
        <div class="ayurveda-content">
          <span class="subtitle">5000+ Years of Wisdom</span>
          <h3>Authentic Ayurveda</h3>
          <p>
            Kerala is the birthplace of authentic Ayurveda, offering natural and holistic healing
            with no harmful side effects. Experience immunity boost, mind-body balance,
            detoxification, and rejuvenation therapies that have stood the test of time.
          </p>
          <ul class="ayurveda-benefits">
            <li>✦ Natural healing with no harmful side effects</li>
            <li>✦ Boosts immunity and longevity</li>
            <li>✦ Effective for chronic diseases</li>
            <li>✦ Mind-body balance and mental health</li>
            <li>✦ Detoxification and rejuvenation</li>
          </ul>
        </div>

        <div class="ayurveda-visual">
          <div class="ayurveda-circle">
            <span class="ayurveda-symbol">🪷</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const features = [
  {
    icon: '💰',
    title: 'Affordable Excellence',
    description:
      'World-class healthcare with internationally accredited hospitals at 60–80% lower cost than Western countries.'
  },
  {
    icon: '👨‍⚕️',
    title: 'Expert Professionals',
    description:
      'Highly skilled doctors with global experience alongside holistic Ayurveda and wellness therapies.'
  },
  {
    icon: '🏥',
    title: 'Specialized Treatments',
    description:
      'Excellence in dental, cardiac surgery, oncology, neurology, orthopedics, and fertility treatments with transparent pricing.'
  },
  {
    icon: '🌴',
    title: 'Scenic Recovery',
    description:
      'Beaches, hill stations, and wellness resorts ideal for stress-free post-treatment recovery.'
  },
  {
    icon: '🗣️',
    title: 'Seamless Experience',
    description:
      'English-speaking staff, medical visa support, and serene recovery destinations for international patients.'
  },
  {
    icon: '🤝',
    title: 'Ethical Care',
    description:
      'High ethical standards, transparent pricing, and personalized care tailored to your needs.'
  }
]
</script>

<style scoped>
/* =========================
   BACKGROUND IMAGE SECTION
========================= */

.bg-section {
  position: relative;
  background-image: url('../assets/images/yoga6.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.bg-overlay {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.content-wrapper {
  position: relative;
  z-index: 1;
}

/* =========================
   TEXT
========================= */

.section-header .text-muted {
  color: rgba(255, 255, 255, 0.75);
}

/* =========================
   FEATURES GRID
========================= */

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 1.5rem;
  margin-bottom: var(--space-xl);
}

.feature-card {
  text-align: center;
  padding: 2.5rem 2rem;
  transition: all var(--transition-base);
}

.feature-card:hover {
  transform: translateY(-8px);
  border-color: rgba(255, 255, 255, 0.3);
  box-shadow: 0 20px 40px rgba(11, 138, 111, 0.25);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.feature-title {
  font-size: 1.25rem;
  margin-bottom: 0.75rem;
  color: var(--color-white);
}

.feature-desc {
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.75);
  line-height: 1.7;
  margin: 0;
}

/* =========================
   AYURVEDA SECTION
========================= */

.ayurveda-highlight {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 4rem;
  align-items: center;
  padding: 4rem;
  background: linear-gradient(
    135deg,
    rgba(11, 138, 111, 0.25),
    rgba(6, 110, 88, 0.15)
  );
  border-radius: var(--radius-lg);
  border: 1px solid rgba(255, 255, 255, 0.12);
}

.ayurveda-content h3 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  color: var(--color-white);
}

.ayurveda-content p {
  color: rgba(255, 255, 255, 0.85);
  margin-bottom: 1.5rem;
}

.ayurveda-benefits {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.ayurveda-benefits li {
  color: rgba(255, 255, 255, 0.9);
  font-size: 1rem;
}

/* =========================
   AYURVEDA VISUAL
========================= */



@keyframes pulse-glow {
  0%, 100% {
    transform: scale(1);
    box-shadow: 0 0 30px rgba(11, 138, 111, 0.5);
  }
  50% {
    transform: scale(1.05);
    box-shadow: 0 0 60px rgba(11, 138, 111, 0.8);
  }
}

/* =========================
   RESPONSIVE
========================= */

@media (max-width: 968px) {
  .ayurveda-highlight {
    grid-template-columns: 1fr;
    text-align: center;
    padding: 2rem;
  }

  .ayurveda-visual {
    order: -1;
  }

  .ayurveda-circle {
    width: 180px;
    height: 180px;
  }

  .ayurveda-symbol {
    font-size: 4rem;
  }

  .ayurveda-benefits {
    align-items: center;
  }
}
</style>
