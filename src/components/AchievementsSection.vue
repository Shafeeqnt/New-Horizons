<template>
  <section id="achievements" class="section section-dark achievements-section">
    <div class="achv-glow achv-glow-1"></div>
    <div class="achv-glow achv-glow-2"></div>

    <div class="container content-wrapper">
      <!-- Header -->
      <div class="section-header">
        <span class="subtitle">Our Partners &amp; Collaborations</span>
        <h2>Building Kerala's Wellness Network, <span class="text-gradient">Together</span></h2>
        <p class="text-muted">
          From master Ayurvedic healers to hospitality brands and healthtech innovators,
          Cure Kerala partners with trusted names across Kerala to deliver a seamless,
          world-class healing journey.
        </p>
      </div>

      <!-- Visible Showcase Grid -->
      <div class="achv-grid">
        <div
          v-for="(item, index) in visibleAchievements"
          :key="index"
          class="achv-card"
          :class="item.size"
          :role="item.size === 'featured' ? 'button' : null"
          :tabindex="item.size === 'featured' ? 0 : null"
          @click="item.size === 'featured' && openModal()"
          @keydown="item.size === 'featured' && (($event.key === 'Enter' || $event.key === ' ') ? (openModal(), $event.preventDefault()) : null)"
        >
          <img :src="item.image" :alt="item.title" class="achv-img" />
          <div class="achv-scrim"></div>
          <div class="achv-chip">{{ item.chip }}</div>
          <div class="achv-info">
            <h3 class="achv-title">{{ item.title }}</h3>
            <p class="achv-caption">{{ item.caption }}</p>
            <span v-if="item.size === 'featured'" class="achv-view-more">
              View All Achievements &amp; Partnerships <span class="achv-view-arrow">→</span>
            </span>
          </div>
        </div>
      </div>

      <!-- Lightbox Modal: reveals the hidden achievements on click -->
      <Teleport to="body">
        <Transition name="modal-fade">
          <div v-if="isModalOpen" class="achv-modal-overlay" @click.self="closeModal">
            <div class="achv-modal">
              <button type="button" class="achv-modal-close" @click="closeModal" aria-label="Close">✕</button>
              <button type="button" class="achv-modal-nav achv-modal-prev" @click="prevSlide" aria-label="Previous">‹</button>
              <button type="button" class="achv-modal-nav achv-modal-next" @click="nextSlide" aria-label="Next">›</button>

              <div class="achv-modal-image-wrap">
                <img :src="activeItem.image" :alt="activeItem.title" class="achv-modal-image" />
              </div>
              <div class="achv-modal-body">
                <span class="achv-modal-chip">{{ activeItem.chip }}</span>
                <h3 class="achv-modal-title">{{ activeItem.title }}</h3>
                <p class="achv-modal-caption">{{ activeItem.caption }}</p>
                <div class="achv-modal-dots">
                  <span
                    v-for="(item, i) in hiddenAchievements"
                    :key="i"
                    class="achv-modal-dot"
                    :class="{ active: i === activeIndex }"
                    @click="activeIndex = i"
                  ></span>
                </div>
              </div>
            </div>
          </div>
        </Transition>
      </Teleport>

      <!-- Partner Brands -->
      <div class="partner-logos-block">
        <p class="partner-logos-label">In Collaboration With</p>
        <div class="partner-logos-grid">
          <div class="partner-logo-card" v-for="(p, i) in partnerBrands" :key="i">
            <div class="partner-logo-frame" :class="{ dark: p.dark }">
              <img :src="p.logo" :alt="p.name" class="partner-logo-img" />
            </div>
            <span class="partner-logo-name">{{ p.name }}</span>
            <span class="partner-logo-role">{{ p.role }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import teamPhoto from '../assets/Acheivements/With our team.PNG'
import exMinisterPhoto from '../assets/Acheivements/With Ex Minister Jaleel of kerala.PNG'
import cmPhoto from '../assets/Acheivements/Wth Cheief Mininster of KERALA.JPG'
import iumlPhoto from '../assets/Acheivements/Wth President of IUML (2).JPG'
import pressPhoto from '../assets/Acheivements/b3c3b2a4-9a97-4aec-8a92-2237b22de40d.JPG'
import ceoSummitPhoto from '../assets/Partners/ceo with ex cheif minister of kerala.webp'
import ceoUnqPhoto from '../assets/Partners/UNQ demo if ceo.jpg'
import rainbowLogo from '../assets/Partners/Rainbow Jeevalayalam Logo.jpg'
import vynaLogo from '../assets/Partners/Vyna Resort Logo.jpg'
import unqLogo from '../assets/Partners/UNQ LOGO.jpg'
import maqLogo from '../assets/Partners/MAQ HOLIDAYS LOGO.png'

const achievements = [
  {
    image: teamPhoto,
    chip: '🤝 Growing Together',
    title: 'Joining Hands with Cure Kerala',
    caption: 'One of many trusted experts now part of the growing Cure Kerala partner network — bringing generations of authentic Ayurvedic mastery to every guest we welcome.',
    size: 'featured',
    hidden: false
  },
  {
    image: ceoSummitPhoto,
    chip: '🚀 Startup Leadership',
    title: 'On Stage at IEDC Summit 2017',
    caption: "Our founder presenting alongside Kerala's Chief Minister at the state's flagship startup summit.",
    size: '',
    hidden: false
  },
  {
    image: ceoUnqPhoto,
    chip: '📱 Healthtech Innovation',
    title: 'Powering Smarter Patient Care',
    caption: 'Our founder showcasing UnQ, a smart hospital queue-management platform — innovation now benefiting Cure Kerala guests.',
    size: '',
    hidden: false
  },
  {
    image: cmPhoto,
    chip: '⭐ State Leadership',
    title: 'With the Chief Minister of Kerala',
    caption: 'Our partner healer, honoured for a lifetime devoted to authentic, time-tested healing.',
    size: '',
    hidden: true
  },
  {
    image: exMinisterPhoto,
    chip: '🏛️ Government Leaders',
    title: "With Hon'ble Ex-Minister of Kerala",
    caption: 'A moment of shared respect amid the tranquil Kerala backwaters.',
    size: '',
    hidden: true
  },
  {
    image: iumlPhoto,
    chip: '🎗️ Community Leaders',
    title: 'With the President of IUML',
    caption: "Recognised and respected across Kerala's community leadership.",
    size: '',
    hidden: true
  },
  {
    image: pressPhoto,
    chip: '📰 In the Press',
    title: 'Featured in Suprabhaatham',
    caption: 'A healing bond with a senior Kerala political leader that made statewide headlines.',
    size: '',
    hidden: true
  }
]

const visibleAchievements = achievements.filter((a) => !a.hidden)
const hiddenAchievements = achievements.filter((a) => a.hidden)

const partnerBrands = [
  { logo: rainbowLogo, name: 'Rainbow Jeevalayam', role: 'Wellness & Community Care Partner' },
  { logo: vynaLogo, name: 'Vyna Hillock Resorts', role: 'Hospitality & Recovery Stay Partner' },
  { logo: unqLogo, name: 'UnQ', role: 'Healthtech Partner', dark: true },
  { logo: maqLogo, name: 'MAQ Holidays', role: 'Travel & Tour Partner' }
]

const isModalOpen = ref(false)
const activeIndex = ref(0)
const activeItem = computed(() => hiddenAchievements[activeIndex.value])

function openModal() {
  activeIndex.value = 0
  isModalOpen.value = true
  document.body.style.overflow = 'hidden'
}

function closeModal() {
  isModalOpen.value = false
  document.body.style.overflow = ''
}

function nextSlide() {
  activeIndex.value = (activeIndex.value + 1) % hiddenAchievements.length
}

function prevSlide() {
  activeIndex.value = (activeIndex.value - 1 + hiddenAchievements.length) % hiddenAchievements.length
}

function handleKeydown(e) {
  if (!isModalOpen.value) return
  if (e.key === 'Escape') closeModal()
  if (e.key === 'ArrowRight') nextSlide()
  if (e.key === 'ArrowLeft') prevSlide()
}

onMounted(() => window.addEventListener('keydown', handleKeydown))
onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
  document.body.style.overflow = ''
})
</script>

<style scoped>
.achievements-section {
  position: relative;
  overflow: hidden;
  background: linear-gradient(180deg, #0f172a 0%, #12241f 50%, #0f172a 100%);
}

.achv-glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  pointer-events: none;
  z-index: 0;
}

.achv-glow-1 {
  width: 500px;
  height: 500px;
  top: -150px;
  left: -150px;
  background: radial-gradient(circle, rgba(79, 189, 176, 0.25), transparent 70%);
}

.achv-glow-2 {
  width: 450px;
  height: 450px;
  bottom: -180px;
  right: -120px;
  background: radial-gradient(circle, rgba(244, 201, 122, 0.2), transparent 70%);
}

.content-wrapper {
  position: relative;
  z-index: 1;
}

.section-header .text-muted {
  color: rgba(255, 255, 255, 0.75);
}

/* Showcase Grid: featured (2x2) + two supporting cards stacked beside it */
.achv-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: minmax(220px, auto);
  gap: 1.25rem;
  margin-bottom: 3rem;
}

.achv-card {
  position: relative;
  grid-column: span 1;
  grid-row: span 1;
  border-radius: 20px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.12);
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.35);
  transition: transform 0.45s cubic-bezier(0.4, 0, 0.2, 1), box-shadow 0.45s ease, border-color 0.45s ease;
}

.achv-card.featured {
  grid-column: span 2;
  grid-row: span 2;
  cursor: pointer;
}

.achv-card:hover {
  transform: translateY(-8px);
  border-color: rgba(244, 201, 122, 0.5);
  box-shadow: 0 25px 60px rgba(31, 122, 107, 0.4);
}

.achv-img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.7s cubic-bezier(0.4, 0, 0.2, 1);
}

.achv-card:hover .achv-img {
  transform: scale(1.08);
}

.achv-scrim {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(6, 12, 11, 0.92) 0%, rgba(6, 12, 11, 0.35) 45%, rgba(6, 12, 11, 0.05) 70%);
}

.achv-chip {
  position: absolute;
  top: 1rem;
  left: 1rem;
  z-index: 2;
  background: rgba(15, 23, 22, 0.65);
  backdrop-filter: blur(6px);
  border: 1px solid rgba(255, 255, 255, 0.25);
  color: #fff;
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.02em;
  padding: 0.4rem 0.9rem;
  border-radius: 999px;
  white-space: nowrap;
}

.achv-info {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  top: 3.75rem;
  z-index: 2;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  overflow: hidden;
}

.achv-title {
  color: #fff;
  font-size: 1.1rem;
  font-weight: 700;
  margin: 0 0 0.4rem;
  line-height: 1.3;
}

.achv-card.featured .achv-title {
  font-size: 1.6rem;
}

.achv-caption {
  color: rgba(255, 255, 255, 0.85);
  font-size: 0.85rem;
  line-height: 1.55;
  margin: 0 0 0.6rem;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.achv-view-more {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.5rem;
  align-self: flex-start;
  max-width: 100%;
  background: linear-gradient(135deg, #f4c97a, #ffe2b3);
  color: #1c2d2a;
  font-size: 0.85rem;
  font-weight: 700;
  line-height: 1.3;
  text-align: center;
  padding: 0.65rem 1.3rem;
  border-radius: 999px;
  box-shadow: 0 8px 25px rgba(244, 201, 122, 0.4);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.achv-card.featured:hover .achv-view-more {
  transform: translateX(4px);
  box-shadow: 0 12px 32px rgba(244, 201, 122, 0.55);
}

.achv-view-arrow {
  transition: transform 0.3s ease;
}

/* Lightbox Modal */
.achv-modal-overlay {
  position: fixed;
  inset: 0;
  z-index: 2000;
  background: rgba(6, 12, 11, 0.88);
  backdrop-filter: blur(6px);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  padding-top: max(2rem, env(safe-area-inset-top));
  padding-bottom: max(2rem, env(safe-area-inset-bottom));
  overflow-y: auto;
}

.achv-modal {
  position: relative;
  width: 100%;
  max-width: 960px;
  max-height: 88vh;
  background: #12211e;
  border: 1px solid rgba(244, 201, 122, 0.25);
  border-radius: 24px;
  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.5);
  overflow: hidden;
  display: grid;
  grid-template-columns: 1.2fr 1fr;
}

.achv-modal-image-wrap {
  position: relative;
  height: 100%;
  min-height: 320px;
  background: #0b1614;
}

.achv-modal-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.achv-modal-body {
  padding: 2.5rem 2.25rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.achv-modal-chip {
  align-self: flex-start;
  background: linear-gradient(135deg, #1f7a6b, #4fbdb0);
  color: #fff;
  font-size: 0.8rem;
  font-weight: 600;
  padding: 0.4rem 1rem;
  border-radius: 999px;
  margin-bottom: 1rem;
}

.achv-modal-title {
  color: #fff;
  font-size: 1.6rem;
  font-weight: 700;
  line-height: 1.3;
  margin: 0 0 1rem;
}

.achv-modal-caption {
  color: rgba(255, 255, 255, 0.85);
  font-size: 1rem;
  line-height: 1.7;
  margin: 0 0 2rem;
}

.achv-modal-dots {
  display: flex;
  gap: 0.5rem;
}

.achv-modal-dot {
  width: 9px;
  height: 9px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.25);
  cursor: pointer;
  transition: all 0.3s ease;
}

.achv-modal-dot.active {
  background: #f4c97a;
  width: 22px;
  border-radius: 5px;
}

.achv-modal-close {
  position: absolute;
  top: 1.25rem;
  right: 1.25rem;
  z-index: 3;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.25);
  background: rgba(6, 12, 11, 0.6);
  color: #fff;
  font-size: 1.1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.achv-modal-close:hover {
  background: #f4c97a;
  color: #1c2d2a;
  border-color: #f4c97a;
}

.achv-modal-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  z-index: 3;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: 1px solid rgba(255, 255, 255, 0.25);
  background: rgba(6, 12, 11, 0.6);
  color: #fff;
  font-size: 1.6rem;
  line-height: 1;
  cursor: pointer;
  transition: all 0.3s ease;
}

.achv-modal-nav:hover {
  background: #f4c97a;
  color: #1c2d2a;
  border-color: #f4c97a;
}

.achv-modal-prev {
  left: 1rem;
}

.achv-modal-next {
  right: 1rem;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.3s ease;
}

.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}

/* Partner Brand Logos */
.partner-logos-block {
  margin-bottom: 3.5rem;
  padding-top: 2.5rem;
  border-top: 1px solid rgba(255, 255, 255, 0.12);
}

.partner-logos-label {
  text-align: center;
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.15em;
  margin: 0 0 2rem;
}

.partner-logos-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.75rem;
}

.partner-logo-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.6rem;
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 18px;
  padding: 1.75rem 2.5rem;
  min-width: 220px;
  transition: all 0.35s ease;
}

.partner-logo-card:hover {
  transform: translateY(-6px);
  background: #ffffff;
  border-color: rgba(244, 201, 122, 0.5);
  box-shadow: 0 20px 45px rgba(0, 0, 0, 0.3);
}

.partner-logo-frame {
  width: 96px;
  height: 96px;
  border-radius: 50%;
  background: #ffffff;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
  transition: background 0.35s ease;
}

.partner-logo-frame.dark {
  background: #0b1614;
  border: 1px solid rgba(255, 255, 255, 0.15);
}

.partner-logo-img {
  width: 78%;
  height: 78%;
  object-fit: contain;
}

.partner-logo-name {
  color: #fff;
  font-size: 1rem;
  font-weight: 700;
  text-align: center;
  transition: color 0.35s ease;
}

.partner-logo-card:hover .partner-logo-name {
  color: #1c2d2a;
}

.partner-logo-role {
  color: rgba(255, 255, 255, 0.65);
  font-size: 0.78rem;
  text-align: center;
  transition: color 0.35s ease;
}

.partner-logo-card:hover .partner-logo-role {
  color: #1f7a6b;
}

/* Responsive */
@media (max-width: 968px) {
  .achv-grid {
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: minmax(240px, auto);
  }

  .achv-card.featured {
    grid-column: span 2;
    grid-row: span 1;
    min-height: 360px;
  }
}

@media (max-width: 640px) {
  .achv-grid {
    grid-template-columns: 1fr;
    grid-auto-rows: minmax(260px, auto);
  }

  .achv-card.featured {
    grid-column: span 1;
    grid-row: span 1;
    min-height: 380px;
  }

  .achv-title {
    font-size: 1rem;
  }

  .achv-card.featured .achv-title {
    font-size: 1.25rem;
  }

  .achv-info {
    top: 3.25rem;
    padding: 1.25rem;
  }

  .achv-caption {
    font-size: 0.8rem;
    -webkit-line-clamp: 2;
  }

  .achv-view-more {
    font-size: 0.78rem;
    padding: 0.55rem 1.1rem;
  }

  .achv-modal-overlay {
    padding: 1rem;
    padding-top: max(1rem, env(safe-area-inset-top));
    padding-bottom: max(1rem, env(safe-area-inset-bottom));
  }

  .achv-modal {
    grid-template-columns: 1fr;
    max-height: 90vh;
    overflow-y: auto;
  }

  .achv-modal-image-wrap {
    min-height: 200px;
  }

  .achv-modal-body {
    padding: 1.75rem 1.5rem;
  }

  .achv-modal-title {
    font-size: 1.3rem;
  }

  .achv-modal-nav {
    width: 38px;
    height: 38px;
    font-size: 1.3rem;
  }

  .partner-logo-card {
    padding: 1.5rem 1.75rem;
    min-width: 160px;
  }

  .partner-logo-frame {
    width: 80px;
    height: 80px;
  }
}
</style>
