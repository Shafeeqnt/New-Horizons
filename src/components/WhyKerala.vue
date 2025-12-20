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

      <!-- Healing Excellence Introduction -->
      <div class="healing-intro">
        <h3 class="healing-intro-title">
          <span class="text-gradient">Kerala:</span> Where Ancient Wisdom Meets Modern Science
        </h3>
        <p class="healing-intro-text">
          Experience the best of both worlds - authentic 5000-year-old Ayurvedic traditions 
          combined with cutting-edge medical technology. Only in God's Own Country.
        </p>
      </div>

      <!-- Dual Healing Sections -->
      <div class="dual-healing-container">
        <!-- Ayurveda Section -->
        <div class="healing-section ayurveda-section">
          <div class="healing-header">
            <div class="healing-badge ayurveda-badge">
              <span class="badge-icon">🪷</span>
              <span class="badge-text">Ancient Wisdom</span>
            </div>
            <h3 class="healing-title">Authentic Ayurveda</h3>
            <p class="healing-subtitle">5000+ Years of Natural Healing</p>
          </div>

          <div class="healing-image-gallery">
            <div class="gallery-main">
              <img :src="ayurvedaImg2" alt="Ayurvedic Care" class="gallery-image main-image" />
              <div class="image-overlay">
                <span class="overlay-text">Traditional Ayurvedic Healing</span>
              </div>
            </div>
            <div class="gallery-secondary">
              <div class="stats-card">
                <div class="stat-item-mini">
                  <span class="stat-number-mini">5000+</span>
                  <span class="stat-label-mini">Years Old</span>
                </div>
                <div class="stat-item-mini">
                  <span class="stat-number-mini">100%</span>
                  <span class="stat-label-mini">Natural</span>
                </div>
              </div>
            </div>
          </div>

          <div class="healing-content">
            <p class="healing-description">
              Kerala is the birthplace of authentic Ayurveda, offering natural and holistic healing 
              that treats the root cause, not just symptoms. Experience time-tested therapies in 
              their most authentic form.
            </p>
            <ul class="healing-benefits">
              <li><span class="benefit-icon">✦</span> Natural healing with zero side effects</li>
              <li><span class="benefit-icon">✦</span> Boosts immunity and longevity</li>
              <li><span class="benefit-icon">✦</span> Effective for chronic diseases</li>
              <li><span class="benefit-icon">✦</span> Mind-body balance & mental wellness</li>
              <li><span class="benefit-icon">✦</span> Detoxification and rejuvenation</li>
              <li><span class="benefit-icon">✦</span> Personalized treatment protocols</li>
            </ul>
          </div>
        </div>

        <!-- Central Connector -->
        <div class="healing-connector">
          <div class="connector-line connector-top"></div>
          <div class="connector-badge">
            <div class="connector-icon">
              <span class="icon-plus">+</span>
            </div>
            <p class="connector-text">
              <strong>Best of Both Worlds</strong>
              <span>Only in Kerala</span>
            </p>
          </div>
          <div class="connector-line connector-bottom"></div>
        </div>

        <!-- Modern Healthcare Section -->
        <div class="healing-section healthcare-section">
          <div class="healing-header">
            <div class="healing-badge healthcare-badge">
              <span class="badge-icon">🏥</span>
              <span class="badge-text">Modern Science</span>
            </div>
            <h3 class="healing-title">World-Class Healthcare</h3>
            <p class="healing-subtitle">Internationally Accredited Excellence</p>
          </div>

          <div class="healing-image-gallery">
            <div class="gallery-main">
              <img :src="modernHealthcareImg" alt="Modern Healthcare" class="gallery-image main-image" />
              <div class="image-overlay">
                <span class="overlay-text">Advanced Technology</span>
              </div>
            </div>
            <div class="gallery-secondary">
              <div class="stats-card">
                <div class="stat-item-mini">
                  <span class="stat-number-mini">JCI</span>
                  <span class="stat-label-mini">Accredited</span>
                </div>
                <div class="stat-item-mini">
                  <span class="stat-number-mini">60-80%</span>
                  <span class="stat-label-mini">Cost Savings</span>
                </div>
              </div>
            </div>
          </div>

          <div class="healing-content">
            <p class="healing-description">
              Kerala boasts internationally accredited hospitals with cutting-edge technology and 
              globally trained specialists. Experience world-class medical care at a fraction of 
              Western costs.
            </p>
            <ul class="healing-benefits">
              <li><span class="benefit-icon">✦</span> JCI & NABH accredited hospitals</li>
              <li><span class="benefit-icon">✦</span> State-of-the-art medical technology</li>
              <li><span class="benefit-icon">✦</span> Internationally trained specialists</li>
              <li><span class="benefit-icon">✦</span> Advanced surgical procedures</li>
              <li><span class="benefit-icon">✦</span> Comprehensive diagnostic facilities</li>
              <li><span class="benefit-icon">✦</span> Transparent pricing & ethical care</li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Bottom CTA -->
      <div class="healing-cta">
        <div class="cta-content">
          <h4 class="cta-title">Experience the Kerala Advantage</h4>
          <p class="cta-text">
            The only destination where you can combine Ayurvedic rejuvenation with advanced medical treatments, 
            all while recovering in paradise.
          </p>
          <a href="#packages" class="cta-button">
            <span>Explore Our Packages</span>
            <span class="button-arrow">→</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import modernHealthcareImg from '../assets/images/modern healt care.jpg'
import ayurvedaImg2 from '../assets/images/aurveda care2.jpg'

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

/* Replaced with new Healing Excellence sections below */

/* =========================
   HEALING EXCELLENCE SECTIONS
========================= */

.healing-intro {
  text-align: center;
  max-width: 900px;
  margin: 0 auto 4rem;
  padding: 3rem 2rem;
  background: linear-gradient(
    135deg,
    rgba(11, 138, 111, 0.15),
    rgba(6, 110, 88, 0.08)
  );
  border-radius: var(--radius-lg);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.healing-intro-title {
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 700;
  color: var(--color-white);
  margin-bottom: 1rem;
  line-height: 1.2;
}

.healing-intro-text {
  font-size: 1.15rem;
  color: rgba(255, 255, 255, 0.85);
  line-height: 1.7;
  margin: 0;
}

/* Dual Healing Container */
.dual-healing-container {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 2rem;
  align-items: start;
  margin-bottom: 4rem;
}

/* Individual Healing Section */
.healing-section {
  background: linear-gradient(
    135deg,
    rgba(11, 138, 111, 0.2),
    rgba(6, 110, 88, 0.1)
  );
  border-radius: var(--radius-lg);
  padding: 3rem;
  border: 1px solid rgba(255, 255, 255, 0.12);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.healing-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, transparent, #4fbdb0, transparent);
  transform: scaleX(0);
  transition: transform 0.6s ease;
}

.healing-section:hover::before {
  transform: scaleX(1);
}

.healing-section:hover {
  transform: translateY(-8px);
  box-shadow: 0 25px 60px rgba(11, 138, 111, 0.3);
  border-color: rgba(255, 255, 255, 0.2);
}

/* Healing Header */
.healing-header {
  text-align: center;
  margin-bottom: 2rem;
}

.healing-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.6rem 1.5rem;
  border-radius: 999px;
  font-size: 0.85rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 1rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.ayurveda-badge {
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
  color: #1c2d2a;
}

.healthcare-badge {
  background: linear-gradient(135deg, #4fbdb0, #66d4c7);
  color: #ffffff;
}

.badge-icon {
  font-size: 1.2rem;
}

.badge-text {
  font-size: 0.75rem;
}

.healing-title {
  font-size: 2.2rem;
  font-weight: 700;
  color: var(--color-white);
  margin-bottom: 0.5rem;
}

.healing-subtitle {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.7);
  font-weight: 500;
}

/* Image Gallery */
.healing-image-gallery {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
  margin-bottom: 2rem;
}

.gallery-main {
  position: relative;
  border-radius: var(--radius-lg);
  overflow: hidden;
  height: 280px;
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
}

.gallery-secondary {
  position: relative;
  border-radius: var(--radius-lg);
  overflow: hidden;
  height: 140px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.25);
}

.gallery-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

.gallery-main:hover .gallery-image,
.gallery-secondary:hover .gallery-image {
  transform: scale(1.1);
}

.image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.7),
    transparent 60%
  );
  display: flex;
  align-items: flex-end;
  padding: 1.5rem;
  opacity: 0;
  transition: opacity 0.4s ease;
}

.gallery-main:hover .image-overlay,
.gallery-secondary:hover .image-overlay {
  opacity: 1;
}

.overlay-text {
  color: white;
  font-size: 1rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

/* Stats Card for Healthcare */
.stats-card {
  height: 100%;
  background: linear-gradient(135deg, #1f7a6b, #4fbdb0);
  display: flex;
  align-items: center;
  justify-content: space-around;
  padding: 1.5rem;
  gap: 1rem;
}

/* Stats Card variation for Ayurveda */
.ayurveda-section .stats-card {
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
}

.ayurveda-section .stat-number-mini,
.ayurveda-section .stat-label-mini {
  color: #1c2d2a;
}

.stat-item-mini {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.stat-number-mini {
  font-size: 1.5rem;
  font-weight: 700;
  color: white;
  line-height: 1;
  margin-bottom: 0.3rem;
}

.stat-label-mini {
  font-size: 0.7rem;
  color: rgba(255, 255, 255, 0.9);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

/* Healing Content */
.healing-content {
  text-align: left;
}

.healing-description {
  color: rgba(255, 255, 255, 0.85);
  line-height: 1.7;
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
}

.healing-benefits {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  list-style: none;
  padding: 0;
}

.healing-benefits li {
  color: rgba(255, 255, 255, 0.9);
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  gap: 0.8rem;
  transition: all 0.3s ease;
  padding: 0.5rem;
  border-radius: 8px;
}

.healing-benefits li:hover {
  background: rgba(255, 255, 255, 0.05);
  transform: translateX(8px);
  color: rgba(255, 255, 255, 1);
}

.benefit-icon {
  color: #f4c97a;
  font-size: 1.1rem;
  flex-shrink: 0;
}

/* Central Connector */
.healing-connector {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2rem 1rem;
  min-width: 180px;
}

.connector-line {
  width: 2px;
  height: 80px;
  background: linear-gradient(
    180deg,
    transparent,
    rgba(244, 201, 122, 0.6),
    transparent
  );
}

.connector-badge {
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
  padding: 2rem 1.5rem;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 15px 40px rgba(244, 201, 122, 0.4);
  margin: 1rem 0;
  animation: pulse-connector 3s ease-in-out infinite;
  position: relative;
}

.connector-badge::before {
  content: '';
  position: absolute;
  inset: -4px;
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
  border-radius: 22px;
  z-index: -1;
  opacity: 0.3;
  animation: pulse-glow 3s ease-in-out infinite;
}

@keyframes pulse-connector {
  0%, 100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
}

@keyframes pulse-glow {
  0%, 100% {
    transform: scale(1);
    opacity: 0.3;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.5;
  }
}

.connector-icon {
  width: 60px;
  height: 60px;
  background: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
}

.icon-plus {
  font-size: 2.5rem;
  font-weight: 700;
  color: #1f7a6b;
  line-height: 1;
}

.connector-text {
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.connector-text strong {
  font-size: 1rem;
  color: #1c2d2a;
  font-weight: 700;
  line-height: 1.2;
}

.connector-text span {
  font-size: 0.8rem;
  color: #1f7a6b;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

/* Healing CTA */
.healing-cta {
  background: linear-gradient(135deg, #1f7a6b, #4fbdb0);
  border-radius: var(--radius-lg);
  padding: 4rem 3rem;
  text-align: center;
  position: relative;
  overflow: hidden;
}

.healing-cta::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -50%;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1), transparent);
  animation: rotate-slow 20s linear infinite;
}

@keyframes rotate-slow {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.cta-content {
  position: relative;
  z-index: 2;
}

.cta-title {
  font-size: 2rem;
  font-weight: 700;
  color: white;
  margin-bottom: 1rem;
}

.cta-text {
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.9);
  max-width: 700px;
  margin: 0 auto 2rem;
  line-height: 1.7;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 1rem;
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
  color: #1c2d2a;
  padding: 1rem 2.5rem;
  border-radius: 999px;
  font-size: 1.05rem;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.3s ease;
  box-shadow: 0 8px 25px rgba(244, 201, 122, 0.4);
}

.cta-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 35px rgba(244, 201, 122, 0.6);
  background: linear-gradient(135deg, #ffe2b3, #f4c97a);
}

.button-arrow {
  font-size: 1.5rem;
  transition: transform 0.3s ease;
}

.cta-button:hover .button-arrow {
  transform: translateX(5px);
}

/* =========================
   RESPONSIVE
========================= */

@media (max-width: 968px) {
  .dual-healing-container {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .healing-connector {
    flex-direction: row;
    padding: 2rem 0;
    min-width: auto;
  }

  .connector-line {
    width: 60px;
    height: 2px;
    background: linear-gradient(
      90deg,
      transparent,
      rgba(244, 201, 122, 0.6),
      transparent
    );
  }

  .connector-badge {
    padding: 1.5rem 2rem;
  }

  .healing-section {
    padding: 2rem;
  }

  .healing-intro {
    padding: 2rem 1.5rem;
    margin-bottom: 3rem;
  }

  .healing-cta {
    padding: 3rem 2rem;
  }

  .gallery-main {
    height: 220px;
  }

  .gallery-secondary {
    height: 120px;
  }
}

@media (max-width: 640px) {
  .healing-intro-title {
    font-size: 1.75rem;
  }

  .healing-title {
    font-size: 1.8rem;
  }

  .healing-section {
    padding: 1.5rem;
  }

  .connector-badge {
    padding: 1.2rem 1.5rem;
  }

  .connector-icon {
    width: 50px;
    height: 50px;
  }

  .icon-plus {
    font-size: 2rem;
  }

  .cta-title {
    font-size: 1.5rem;
  }

  .cta-text {
    font-size: 1rem;
  }
}
</style>
