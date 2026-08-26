<template>
  <section class="section culture-discover-section">
    <div class="container">
      <div class="section-wrapper">
        <!-- Left: 3D Luminous Switch Component -->
        <div class="discover-trigger">
          <div class="trigger-content">
            <h2 class="trigger-title">Discover Kerala's <span class="text-gradient">Rich Heritage</span></h2>
            <p class="trigger-subtitle">Unveil the vibrant culture and exquisite cuisine</p>
            
            <!-- 3D Switch Button -->
            <div class="switch-container" @click="openModal">
              <div class="switch-glow"></div>
              <div class="switch-button">
                <div class="switch-track">
                  <div class="switch-thumb">
                    <span class="switch-icon">✨</span>
                  </div>
                </div>
                <span class="switch-label">Swipe to Explore</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Right: Living Heritage Orbit -->
        <div class="globe-section">
          <div class="culture-orbit">
            <div class="orbit-ring ring-outer"></div>
            <div class="orbit-ring ring-inner"></div>

            <div class="orbit-center">
              <span class="orbit-center-icon">🪔</span>
              <span class="orbit-center-label">Living<br />Heritage</span>
            </div>

            <div class="orbit-group">
              <div
                class="orbit-item"
                v-for="(item, index) in heritageItems"
                :key="item.label"
                :style="{ transform: `rotate(${index * (360 / heritageItems.length)}deg) translateX(var(--orbit-radius)) rotate(${-index * (360 / heritageItems.length)}deg)` }"
              >
                <div class="orbit-item-inner">
                  <span class="orbit-icon">{{ item.icon }}</span>
                  <span class="orbit-label">{{ item.label }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Impressive Popup Modal -->
      <Transition name="modal">
        <div v-if="isModalOpen" class="modal-overlay" @click="closeModal">
          <div class="modal-container" @click.stop>
            <button class="modal-close" @click="closeModal">
              <span>✕</span>
            </button>
            
            <div class="modal-content">
              <div class="culture-content">
                <div class="culture-text">
                  <span class="subtitle">Rich Heritage</span>
                  <h2>Kerala's Vibrant <span class="text-gradient">Culture</span></h2>
                  <p>Kerala's culture is a vibrant blend of art, festivals, and warm hospitality. Experience ancient art forms, colorful celebrations, and a unique cultural tapestry woven over millennia.</p>
                  
                  <div class="culture-highlights">
                    <div class="culture-item" v-for="(item, index) in cultureItems" :key="index" :style="{ animationDelay: `${index * 0.1}s` }">
                      <span class="culture-icon">{{ item.icon }}</span>
                      <div>
                        <h4>{{ item.title }}</h4>
                        <p>{{ item.description }}</p>
                      </div>
                    </div>
                  </div>
                </div>
                
                <div class="culture-food">
                  <div class="food-card">
                    <div class="food-badge">Bon Appétit</div>
                    <h3>Kerala <span class="text-accent">Cuisine</span></h3>
                    <p class="food-intro">Spices are the soul of cuisine, infusing every dish with rich aromatic flavors</p>
                    <div class="food-items">
                      <div class="food-item" v-for="(food, index) in foodItems" :key="index" :style="{ animationDelay: `${index * 0.08}s` }">
                        {{ food }}
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </Transition>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const isModalOpen = ref(false)

const cultureItems = [
  { icon: '🎭', title: 'Ancient Art Forms', description: 'Kathakali, Mohiniyattam, and Theyyam performances' },
  { icon: '🎉', title: 'Vibrant Festivals', description: 'Onam, Eid, Christmas celebrated together' },
  { icon: '🌿', title: 'Living Traditions', description: 'Ayurveda, spice cultivation, martial arts' },
  { icon: '🤝', title: 'Warm Hospitality', description: 'Harmonious blend of Hindu, Muslim, and Christian communities' }
]

const heritageItems = [
  { icon: '🎭', label: 'Kathakali' },
  { icon: '🛶', label: 'Backwaters' },
  { icon: '🌿', label: 'Ayurveda' },
  { icon: '🎉', label: 'Onam' },
  { icon: '🐘', label: 'Festivals' },
  { icon: '🍛', label: 'Sadya Feast' }
]

const foodItems = [
  '🍛 Beef curry, spicy chicken, mutton porotta',
  '🦐 Fish curry, prawns in coconut gravies',
  '🍌 Kerala Sadya vegetarian feast',
  '🥘 Kozhikode-style biryani',
  '🍘 Banana chips, cutlets, samosas',
  '🥮 Thalasseri chicken & mutton rolls'
]

const openModal = () => {
  isModalOpen.value = true
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  isModalOpen.value = false
  document.body.style.overflow = ''
}

</script>

<style scoped>
.culture-discover-section {
  background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%);
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  padding: 4rem 2rem;
}

.culture-discover-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 50%, rgba(139, 92, 246, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 50%, rgba(236, 72, 153, 0.1) 0%, transparent 50%);
  animation: pulse-bg 8s ease-in-out infinite;
}

@keyframes pulse-bg {
  0%, 100% { opacity: 0.5; }
  50% { opacity: 1; }
}

.section-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  max-width: 1400px;
  width: 100%;
  position: relative;
  z-index: 1;
}

.discover-trigger {
  text-align: center;
}

.trigger-content {
  max-width: 600px;
  margin: 0 auto;
}

.trigger-title {
  font-size: 3.5rem;
  font-weight: 700;
  color: #fff;
  margin-bottom: 1rem;
  text-shadow: 0 0 30px rgba(139, 92, 246, 0.5);
  line-height: 1.2;
}

.text-gradient {
  background: linear-gradient(135deg, #8b5cf6, #ec4899);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.trigger-subtitle {
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 3rem;
}

/* 3D Switch Component */
.switch-container {
  position: relative;
  display: inline-block;
  cursor: pointer;
  perspective: 1000px;
}

.switch-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(139, 92, 246, 0.4) 0%, transparent 70%);
  border-radius: 50%;
  animation: glow-pulse 2s ease-in-out infinite;
  pointer-events: none;
}

@keyframes glow-pulse {
  0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 0.5; }
  50% { transform: translate(-50%, -50%) scale(1.2); opacity: 0.8; }
}

.switch-button {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.switch-track {
  width: 200px;
  height: 100px;
  background: linear-gradient(145deg, #1e293b, #0f172a);
  border-radius: 50px;
  padding: 10px;
  box-shadow: 
    inset 0 4px 10px rgba(0, 0, 0, 0.5),
    0 0 20px rgba(139, 92, 246, 0.3),
    0 0 40px rgba(236, 72, 153, 0.2);
  position: relative;
  transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
  transform-style: preserve-3d;
}

.switch-container:hover .switch-track {
  transform: rotateY(10deg) rotateX(5deg);
  box-shadow: 
    inset 0 4px 10px rgba(0, 0, 0, 0.5),
    0 0 30px rgba(139, 92, 246, 0.5),
    0 0 60px rgba(236, 72, 153, 0.4);
}

.switch-thumb {
  width: 80px;
  height: 80px;
  background: linear-gradient(145deg, #8b5cf6, #ec4899);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 
    0 8px 20px rgba(139, 92, 246, 0.6),
    0 0 40px rgba(236, 72, 153, 0.4),
    inset 0 -2px 10px rgba(0, 0, 0, 0.3);
  animation: float 3s ease-in-out infinite;
  transition: all 0.3s ease;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

.switch-container:hover .switch-thumb {
  transform: scale(1.1) translateY(-5px);
  box-shadow: 
    0 12px 30px rgba(139, 92, 246, 0.8),
    0 0 60px rgba(236, 72, 153, 0.6),
    inset 0 -2px 10px rgba(0, 0, 0, 0.3);
}

.switch-icon {
  font-size: 2rem;
  animation: sparkle 2s ease-in-out infinite;
}

@keyframes sparkle {
  0%, 100% { transform: rotate(0deg) scale(1); }
  25% { transform: rotate(-10deg) scale(1.1); }
  75% { transform: rotate(10deg) scale(1.1); }
}

.switch-label {
  font-size: 1.1rem;
  font-weight: 600;
  color: #fff;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-shadow: 0 0 10px rgba(139, 92, 246, 0.8);
  animation: label-glow 2s ease-in-out infinite;
}

@keyframes label-glow {
  0%, 100% { opacity: 0.7; }
  50% { opacity: 1; }
}

/* Globe Section */
.globe-section {
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Living Heritage Orbit */
.culture-orbit {
  position: relative;
  width: 560px;
  height: 560px;
  --orbit-radius: 215px;
}

.orbit-ring {
  position: absolute;
  top: 50%;
  left: 50%;
  border-radius: 50%;
  pointer-events: none;
}

.ring-outer {
  width: 520px;
  height: 520px;
  transform: translate(-50%, -50%);
  border: 1px dashed rgba(255, 215, 0, 0.18);
  animation: ring-spin 50s linear infinite;
}

.ring-inner {
  width: 380px;
  height: 380px;
  transform: translate(-50%, -50%);
  border: 1px dashed rgba(139, 92, 246, 0.2);
  animation: ring-spin 35s linear infinite reverse;
}

@keyframes ring-spin {
  to { transform: translate(-50%, -50%) rotate(360deg); }
}

.orbit-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 3;
  width: 170px;
  height: 170px;
  border-radius: 50%;
  background: linear-gradient(145deg, #1e293b, #0f172a);
  border: 2px solid rgba(255, 215, 0, 0.35);
  box-shadow:
    0 0 40px rgba(139, 92, 246, 0.5),
    0 0 80px rgba(236, 72, 153, 0.3),
    inset 0 0 30px rgba(255, 255, 255, 0.05);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.4rem;
  animation: center-pulse 4s ease-in-out infinite;
}

@keyframes center-pulse {
  0%, 100% { box-shadow: 0 0 40px rgba(139, 92, 246, 0.5), 0 0 80px rgba(236, 72, 153, 0.3), inset 0 0 30px rgba(255, 255, 255, 0.05); }
  50% { box-shadow: 0 0 60px rgba(139, 92, 246, 0.7), 0 0 110px rgba(236, 72, 153, 0.5), inset 0 0 30px rgba(255, 255, 255, 0.08); }
}

.orbit-center-icon {
  font-size: 3.2rem;
  line-height: 1;
  filter: drop-shadow(0 0 15px rgba(255, 215, 0, 0.6));
  animation: flicker 2s ease-in-out infinite;
}

@keyframes flicker {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.85; transform: scale(1.08); }
}

.orbit-center-label {
  font-size: 0.7rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: #fff;
  text-align: center;
  line-height: 1.3;
  opacity: 0.85;
}

.orbit-group {
  position: absolute;
  inset: 0;
  z-index: 2;
  animation: orbit-spin 34s linear infinite;
}

@keyframes orbit-spin {
  to { transform: rotate(360deg); }
}

.orbit-item {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
}

.orbit-item-inner {
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
  background: rgba(255, 255, 255, 0.07);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 18px;
  padding: 0.85rem 0.9rem;
  min-width: 88px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.35);
  animation: orbit-counter 34s linear infinite;
  transition: background 0.3s ease, border-color 0.3s ease;
}

@keyframes orbit-counter {
  from { transform: translate(-50%, -50%) rotate(0deg); }
  to { transform: translate(-50%, -50%) rotate(-360deg); }
}

.orbit-item-inner:hover {
  background: rgba(255, 255, 255, 0.16);
  border-color: rgba(255, 215, 0, 0.4);
}

.culture-orbit:hover .orbit-group,
.culture-orbit:hover .orbit-item-inner {
  animation-play-state: paused;
}

.orbit-icon {
  font-size: 1.7rem;
  line-height: 1;
  filter: drop-shadow(0 0 8px rgba(255, 215, 0, 0.3));
}

.orbit-label {
  font-size: 0.68rem;
  font-weight: 600;
  color: #fff;
  text-align: center;
  letter-spacing: 0.03em;
  white-space: nowrap;
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.85);
  backdrop-filter: blur(10px);
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  overflow-y: auto;
}

.modal-container {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.95) 0%, rgba(248, 249, 250, 0.95) 100%);
  border-radius: 24px;
  max-width: 1200px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  box-shadow: 
    0 25px 50px rgba(0, 0, 0, 0.3),
    0 0 100px rgba(139, 92, 246, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.modal-close {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: linear-gradient(145deg, #8b5cf6, #ec4899);
  border: none;
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(139, 92, 246, 0.4);
}

.modal-close:hover {
  transform: rotate(90deg) scale(1.1);
  box-shadow: 0 6px 25px rgba(139, 92, 246, 0.6);
}

.modal-content {
  padding: 4rem;
}

.culture-content {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 4rem;
  align-items: start;
}

.culture-text .subtitle {
  color: #8b5cf6;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 2px;
  font-size: 0.9rem;
}

.culture-text h2 {
  margin-bottom: 1rem;
  font-size: 2.5rem;
  color: #1a202c;
}

.text-accent {
  color: #ec4899;
}

.culture-text > p {
  color: #4a5568;
  font-size: 1.1rem;
  margin-bottom: 2rem;
  line-height: 1.8;
}

.culture-highlights {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}

.culture-item {
  display: flex;
  gap: 1rem;
  align-items: flex-start;
  opacity: 0;
  animation: slideInUp 0.6s ease forwards;
}

@keyframes slideInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.culture-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.culture-item h4 {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.25rem;
  color: #1a202c;
}

.culture-item p {
  font-size: 0.85rem;
  color: #4a5568;
  margin: 0;
  line-height: 1.6;
}

.food-card {
  background: #ffffff;
  border-radius: 16px;
  padding: 2.5rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  position: relative;
  overflow: hidden;
  animation: scaleIn 0.5s ease forwards;
}

@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.9);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.food-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, #f59e0b, #d97706);
}

.food-badge {
  display: inline-block;
  background: linear-gradient(90deg, #f59e0b, #d97706);
  color: #1a202c;
  padding: 0.25rem 1rem;
  border-radius: 50px;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.food-card h3 {
  font-size: 1.75rem;
  margin-bottom: 0.5rem;
  color: #1a202c;
}

.food-intro {
  font-size: 0.95rem;
  color: #4a5568;
  font-style: italic;
  margin-bottom: 1.5rem;
}

.food-items {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.food-item {
  padding: 0.75rem 1rem;
  background: #f7fafc;
  border-radius: 8px;
  font-size: 0.9rem;
  color: #1a202c;
  transition: all 0.3s ease;
  opacity: 0;
  animation: slideInRight 0.5s ease forwards;
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.food-item:hover {
  background: #8b5cf6;
  color: #ffffff;
  transform: translateX(5px);
}

/* Modal Transitions */
.modal-enter-active {
  animation: modalFadeIn 0.4s ease;
}

.modal-leave-active {
  animation: modalFadeOut 0.3s ease;
}

@keyframes modalFadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes modalFadeOut {
  from { opacity: 1; }
  to { opacity: 0; }
}

.modal-enter-active .modal-container {
  animation: modalSlideIn 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.modal-leave-active .modal-container {
  animation: modalSlideOut 0.3s ease;
}

@keyframes modalSlideIn {
  from {
    transform: scale(0.8) translateY(50px);
    opacity: 0;
  }
  to {
    transform: scale(1) translateY(0);
    opacity: 1;
  }
}

@keyframes modalSlideOut {
  from {
    transform: scale(1) translateY(0);
    opacity: 1;
  }
  to {
    transform: scale(0.8) translateY(50px);
    opacity: 0;
  }
}

@media (max-width: 968px) {
  .section-wrapper {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .trigger-title {
    font-size: 2.5rem;
  }
  
  .switch-track {
    width: 160px;
    height: 80px;
  }
  
  .switch-thumb {
    width: 60px;
    height: 60px;
  }

  .culture-orbit {
    width: 400px;
    height: 400px;
    --orbit-radius: 150px;
  }

  .ring-outer {
    width: 360px;
    height: 360px;
  }

  .ring-inner {
    width: 260px;
    height: 260px;
  }

  .orbit-center {
    width: 130px;
    height: 130px;
  }

  .orbit-center-icon {
    font-size: 2.4rem;
  }

  .orbit-item-inner {
    padding: 0.6rem 0.7rem;
    min-width: 72px;
  }

  .orbit-icon {
    font-size: 1.3rem;
  }

  .orbit-label {
    font-size: 0.6rem;
  }

  .modal-content {
    padding: 2rem;
  }
  
  .culture-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .culture-highlights {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 480px) {
  .culture-discover-section {
    padding: 3rem 1rem;
  }

  .trigger-title {
    font-size: 1.9rem;
  }

  .trigger-subtitle {
    font-size: 1rem;
    margin-bottom: 2rem;
  }

  .switch-track {
    width: 130px;
    height: 65px;
  }

  .switch-thumb {
    width: 48px;
    height: 48px;
  }

  .switch-icon {
    font-size: 1.5rem;
  }

  .culture-orbit {
    width: 280px;
    height: 280px;
    --orbit-radius: 100px;
  }

  .ring-outer {
    width: 250px;
    height: 250px;
  }

  .ring-inner {
    width: 175px;
    height: 175px;
  }

  .orbit-center {
    width: 92px;
    height: 92px;
  }

  .orbit-center-icon {
    font-size: 1.7rem;
  }

  .orbit-center-label {
    font-size: 0.55rem;
  }

  .orbit-item-inner {
    padding: 0.4rem 0.5rem;
    min-width: 52px;
  }

  .orbit-icon {
    font-size: 1rem;
  }

  .orbit-label {
    display: none;
  }

  .modal-overlay {
    padding: 1rem;
  }

  .modal-content {
    padding: 1.5rem;
  }

  .modal-close {
    width: 40px;
    height: 40px;
    top: 1rem;
    right: 1rem;
  }

  .culture-text h2 {
    font-size: 1.75rem;
  }

  .food-card {
    padding: 1.75rem;
  }
}
</style>