<template>
  <section class="our-story">
    <div class="story-container">
      <!-- Section Header -->
      <div class="story-header">
        <span class="story-badge">Our Journey</span>
        <h2 class="story-title">
          Where <span class="text-gradient">Passion</span> Meets <span class="text-gradient">Purpose</span>
        </h2>
        <p class="story-intro">
          Two visionaries united by a shared dream: to transform healing into a superpower 
          through the ancient wisdom of Kerala and modern healthcare excellence.
        </p>
      </div>

      <!-- Founders Section -->
      <div class="founders-grid">
        <!-- Founder 1: Tourism Consultant -->
        <div class="founder-card" data-founder="1">
          <div class="founder-image-wrapper">
            <div class="image-glow"></div>
            <div class="founder-image founder-1">
              <!-- Placeholder for founder image - will be added later -->
              <div class="image-placeholder">
                <span class="placeholder-icon">🌍</span>
              </div>
            </div>
            <div class="founder-badge">Tourism Expert</div>
          </div>
          <div class="founder-content">
            <h3 class="founder-name">The Explorer</h3>
            <p class="founder-role">Global Tourism Consultant</p>
            <div class="founder-stats">
              <div class="stat-item">
                <span class="stat-value">50+</span>
                <span class="stat-label">Countries Visited</span>
              </div>
              <div class="stat-item">
                <span class="stat-value">15+</span>
                <span class="stat-label">Years Experience</span>
              </div>
            </div>
            <p class="founder-story">
              Having traversed the globe and witnessed diverse healing traditions, 
              discovered Kerala's unparalleled potential to blend wellness, culture, 
              and authentic experiences into transformative journeys.
            </p>
          </div>
        </div>

        <!-- Connection Element -->
        <div class="connection-element">
          <div class="connection-line"></div>
          <div class="connection-icon">
            <span class="icon-heart">❤️</span>
            <span class="icon-text">United Vision</span>
          </div>
          <div class="connection-line"></div>
        </div>

        <!-- Founder 2: Healthcare Professional -->
        <div class="founder-card" data-founder="2">
          <div class="founder-image-wrapper">
            <div class="image-glow"></div>
            <div class="founder-image founder-2">
              <!-- Placeholder for founder image - will be added later -->
              <div class="image-placeholder">
                <span class="placeholder-icon">🏥</span>
              </div>
            </div>
            <div class="founder-badge">Healthcare Pioneer</div>
          </div>
          <div class="founder-content">
            <h3 class="founder-name">The Healer</h3>
            <p class="founder-role">Medical Tourism Specialist</p>
            <div class="founder-stats">
              <div class="stat-item">
                <span class="stat-value">1000+</span>
                <span class="stat-label">Lives Transformed</span>
              </div>
              <div class="stat-item">
                <span class="stat-value">20+</span>
                <span class="stat-label">Partner Hospitals</span>
              </div>
            </div>
            <p class="founder-story">
              With deep roots in Kerala's healthcare ecosystem and a passion for 
              holistic healing, bridges the gap between traditional Ayurveda and 
              modern medicine to create comprehensive wellness solutions.
            </p>
          </div>
        </div>
      </div>

      <!-- Mission Statement -->
      <div class="mission-statement">
        <div class="mission-content">
          <div class="mission-icon">✨</div>
          <h3 class="mission-title">Our Shared Mission</h3>
          <p class="mission-text">
            Together, we've created Cure Kerala to make healing a superpower accessible to all.
            By combining world-class medical expertise, authentic Ayurvedic traditions, and the 
            serene beauty of Kerala, we offer transformative experiences that heal the body, 
            calm the mind, and rejuvenate the spirit.
          </p>
          <div class="mission-values">
            <div class="value-item">
              <span class="value-icon">🌿</span>
              <span class="value-text">Authentic Healing</span>
            </div>
            <div class="value-item">
              <span class="value-icon">🤝</span>
              <span class="value-text">Trusted Partnership</span>
            </div>
            <div class="value-item">
              <span class="value-icon">💫</span>
              <span class="value-text">Transformative Care</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Decorative Elements -->
    <div class="story-decorations">
      <div class="deco-circle deco-1"></div>
      <div class="deco-circle deco-2"></div>
      <div class="deco-circle deco-3"></div>
    </div>
  </section>
</template>

<script setup>
// Component logic can be added here if needed
</script>

<style scoped>
.our-story {
  position: relative;
  padding: 8rem 2rem;
  background: linear-gradient(180deg, 
    #f8f9fa 0%, 
    #ffffff 50%, 
    #f0f7f6 100%
  );
  overflow: hidden;
}

.story-container {
  max-width: 1400px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

/* Header Styles */
.story-header {
  text-align: center;
  margin-bottom: 5rem;
}

.story-badge {
  display: inline-block;
  background: linear-gradient(135deg, #1f7a6b, #4fbdb0);
  color: white;
  padding: 0.6rem 1.8rem;
  border-radius: 999px;
  font-size: 0.85rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 15px rgba(31, 122, 107, 0.3);
}

.story-title {
  font-size: clamp(2.5rem, 4vw, 3.5rem);
  font-weight: 700;
  color: #1c2d2a;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.text-gradient {
  background: linear-gradient(120deg, #1f7a6b, #4fbdb0, #f4c97a);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.story-intro {
  font-size: 1.15rem;
  color: #5a6c6a;
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.7;
}

/* Founders Grid */
.founders-grid {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: 3rem;
  align-items: center;
  margin-bottom: 5rem;
}

.founder-card {
  background: white;
  border-radius: 24px;
  padding: 2.5rem;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.08);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.founder-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, #1f7a6b, #4fbdb0, #f4c97a);
  transform: scaleX(0);
  transition: transform 0.4s ease;
}

.founder-card:hover::before {
  transform: scaleX(1);
}

.founder-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 60px rgba(31, 122, 107, 0.15);
}

/* Founder Image */
.founder-image-wrapper {
  position: relative;
  margin-bottom: 2rem;
}

.founder-image {
  width: 200px;
  height: 200px;
  margin: 0 auto;
  border-radius: 50%;
  overflow: hidden;
  position: relative;
  border: 4px solid #f4c97a;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
}

.image-placeholder {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #e0f2f1, #b2dfdb);
  display: flex;
  align-items: center;
  justify-content: center;
}

.placeholder-icon {
  font-size: 5rem;
  opacity: 0.7;
}

.image-glow {
  position: absolute;
  inset: -20px;
  background: radial-gradient(circle, rgba(79, 189, 176, 0.3), transparent);
  z-index: -1;
  animation: pulse 3s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 0.5; transform: scale(1); }
  50% { opacity: 0.8; transform: scale(1.1); }
}

.founder-badge {
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
  color: #1c2d2a;
  padding: 0.5rem 1.5rem;
  border-radius: 999px;
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  box-shadow: 0 4px 15px rgba(244, 201, 122, 0.4);
  white-space: nowrap;
}

/* Founder Content */
.founder-content {
  text-align: center;
}

.founder-name {
  font-size: 1.8rem;
  font-weight: 700;
  color: #1c2d2a;
  margin-bottom: 0.5rem;
}

.founder-role {
  font-size: 1rem;
  color: #1f7a6b;
  font-weight: 600;
  margin-bottom: 1.5rem;
}

.founder-stats {
  display: flex;
  gap: 2rem;
  justify-content: center;
  margin-bottom: 1.5rem;
  padding: 1.5rem 0;
  border-top: 1px solid #e0e0e0;
  border-bottom: 1px solid #e0e0e0;
}

.stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.stat-value {
  font-size: 1.8rem;
  font-weight: 700;
  color: #1f7a6b;
  line-height: 1;
  margin-bottom: 0.3rem;
}

.stat-label {
  font-size: 0.8rem;
  color: #5a6c6a;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.founder-story {
  font-size: 0.95rem;
  color: #5a6c6a;
  line-height: 1.7;
  text-align: left;
}

/* Connection Element */
.connection-element {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  padding: 0 1rem;
}

.connection-line {
  width: 2px;
  height: 60px;
  background: linear-gradient(180deg, transparent, #4fbdb0, transparent);
}

.connection-icon {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  background: white;
  padding: 1.5rem;
  border-radius: 50%;
  box-shadow: 0 8px 25px rgba(31, 122, 107, 0.2);
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

.icon-heart {
  font-size: 2.5rem;
  animation: heartbeat 2s ease-in-out infinite;
}

@keyframes heartbeat {
  0%, 100% { transform: scale(1); }
  25% { transform: scale(1.1); }
  50% { transform: scale(1); }
}

.icon-text {
  font-size: 0.7rem;
  font-weight: 600;
  color: #1f7a6b;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  white-space: nowrap;
}

/* Mission Statement */
.mission-statement {
  background: linear-gradient(135deg, #1f7a6b, #4fbdb0);
  border-radius: 32px;
  padding: 4rem 3rem;
  color: white;
  position: relative;
  overflow: hidden;
}

.mission-statement::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -50%;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1), transparent);
  animation: rotate 20s linear infinite;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.mission-content {
  position: relative;
  z-index: 2;
  text-align: center;
}

.mission-icon {
  font-size: 3.5rem;
  margin-bottom: 1.5rem;
  animation: sparkle 2s ease-in-out infinite;
}

@keyframes sparkle {
  0%, 100% { opacity: 1; transform: scale(1) rotate(0deg); }
  50% { opacity: 0.8; transform: scale(1.1) rotate(10deg); }
}

.mission-title {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
}

.mission-text {
  font-size: 1.1rem;
  line-height: 1.8;
  max-width: 900px;
  margin: 0 auto 2.5rem;
  opacity: 0.95;
}

.mission-values {
  display: flex;
  gap: 3rem;
  justify-content: center;
  flex-wrap: wrap;
}

.value-item {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  background: rgba(255, 255, 255, 0.15);
  padding: 1rem 1.8rem;
  border-radius: 999px;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

.value-item:hover {
  background: rgba(255, 255, 255, 0.25);
  transform: translateY(-3px);
}

.value-icon {
  font-size: 1.5rem;
}

.value-text {
  font-size: 0.95rem;
  font-weight: 600;
  white-space: nowrap;
}

/* Decorative Elements */
.story-decorations {
  position: absolute;
  inset: 0;
  pointer-events: none;
  overflow: hidden;
}

.deco-circle {
  position: absolute;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(79, 189, 176, 0.1), transparent);
}

.deco-1 {
  width: 400px;
  height: 400px;
  top: -200px;
  left: -100px;
  animation: float 15s ease-in-out infinite;
}

.deco-2 {
  width: 300px;
  height: 300px;
  bottom: -150px;
  right: -50px;
  animation: float 12s ease-in-out infinite reverse;
}

.deco-3 {
  width: 250px;
  height: 250px;
  top: 50%;
  right: 10%;
  animation: float 18s ease-in-out infinite;
}

/* Responsive Design */
@media (max-width: 1024px) {
  .founders-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .connection-element {
    flex-direction: row;
  }

  .connection-line {
    width: 60px;
    height: 2px;
    background: linear-gradient(90deg, transparent, #4fbdb0, transparent);
  }

  .founder-stats {
    gap: 1.5rem;
  }
}

@media (max-width: 768px) {
  .our-story {
    padding: 5rem 1.5rem;
  }

  .story-header {
    margin-bottom: 3rem;
  }

  .founder-card {
    padding: 2rem 1.5rem;
  }

  .founder-image {
    width: 160px;
    height: 160px;
  }

  .placeholder-icon {
    font-size: 4rem;
  }

  .mission-statement {
    padding: 3rem 2rem;
  }

  .mission-values {
    gap: 1rem;
  }

  .value-item {
    padding: 0.8rem 1.2rem;
  }
}

@media (max-width: 480px) {
  .our-story {
    padding: 4rem 1rem;
  }

  .founder-card {
    padding: 1.5rem 1.25rem;
  }

  .founder-image {
    width: 130px;
    height: 130px;
  }

  .placeholder-icon {
    font-size: 3.5rem;
  }

  .founder-name {
    font-size: 1.5rem;
  }

  .founder-stats {
    gap: 1rem;
  }

  .stat-value {
    font-size: 1.4rem;
  }

  .mission-statement {
    padding: 2rem 1.25rem;
  }

  .mission-title {
    font-size: 1.5rem;
  }

  .mission-text {
    font-size: 1rem;
  }

  .mission-values {
    flex-direction: column;
    align-items: stretch;
  }

  .value-item {
    justify-content: center;
  }
}
</style>
