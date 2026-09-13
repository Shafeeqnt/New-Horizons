<template>
  <section id="achievements" class="section section-dark achievements-section">
    <div class="achv-glow achv-glow-1"></div>
    <div class="achv-glow achv-glow-2"></div>

    <div class="container content-wrapper">
      <!-- Header -->
      <div class="section-header">
        <span class="subtitle">Heritage &amp; Recognition</span>
        <h2>A Healer Trusted by <span class="text-gradient">Kerala's Finest</span></h2>
        <p class="text-muted">
          With years of devoted Ayurvedic practice, our master healer has earned the trust of
          political leaders, community icons, and the press — and now proudly stands
          hand-in-hand with Cure Kerala.
        </p>
      </div>

      <!-- Bento Showcase Grid -->
      <div class="achv-grid">
        <div
          v-for="(item, index) in achievements"
          :key="index"
          class="achv-card"
          :class="item.size"
        >
          <img :src="item.image" :alt="item.title" class="achv-img" />
          <div class="achv-scrim"></div>
          <div class="achv-chip">{{ item.chip }}</div>
          <div class="achv-info">
            <h3 class="achv-title">{{ item.title }}</h3>
            <p class="achv-caption">{{ item.caption }}</p>
          </div>
        </div>
      </div>

      <!-- Trust Strip -->
      <div class="achv-trust-strip">
        <div class="trust-pill" v-for="(t, i) in trustPoints" :key="i">
          <span class="trust-icon">{{ t.icon }}</span>
          <span class="trust-text">{{ t.text }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import teamPhoto from '../assets/Acheivements/With our team.PNG'
import exMinisterPhoto from '../assets/Acheivements/With Ex Minister Jaleel of kerala.PNG'
import cmPhoto from '../assets/Acheivements/Wth Cheief Mininster of KERALA.JPG'
import iumlPhoto from '../assets/Acheivements/Wth President of IUML (2).JPG'
import pressPhoto from '../assets/Acheivements/b3c3b2a4-9a97-4aec-8a92-2237b22de40d.JPG'

const achievements = [
  {
    image: teamPhoto,
    chip: '🤝 Our Partnership',
    title: 'Joining Hands with Cure Kerala',
    caption: 'Our master healer is now proudly part of the Cure Kerala family, bringing generations of authentic Ayurvedic mastery to every guest we welcome.',
    size: 'featured'
  },
  {
    image: exMinisterPhoto,
    chip: '🏛️ Government Leaders',
    title: "With Hon'ble Ex-Minister of Kerala",
    caption: 'A moment of shared respect amid the tranquil Kerala backwaters.',
    size: ''
  },
  {
    image: cmPhoto,
    chip: '⭐ State Leadership',
    title: 'With the Chief Minister of Kerala',
    caption: 'Honoured for a lifetime devoted to authentic, time-tested healing.',
    size: ''
  },
  {
    image: iumlPhoto,
    chip: '🎗️ Community Leaders',
    title: 'With the President of IUML',
    caption: 'Recognised and respected across Kerala\'s community leadership.',
    size: ''
  },
  {
    image: pressPhoto,
    chip: '📰 In the Press',
    title: 'Featured in Suprabhaatham',
    caption: 'His healing bond with a senior Kerala political leader made statewide headlines.',
    size: ''
  }
]

const trustPoints = [
  { icon: '🪷', text: 'Decades of Ayurvedic Mastery' },
  { icon: '👑', text: 'Trusted by Public Leaders' },
  { icon: '📰', text: 'Featured in Regional Media' },
  { icon: '🤝', text: 'Now Part of Cure Kerala' }
]
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

/* Bento Grid */
.achv-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 260px;
  gap: 1.25rem;
  margin-bottom: 3.5rem;
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
  z-index: 2;
  padding: 1.5rem;
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
  margin: 0;
  max-height: 0;
  opacity: 0;
  overflow: hidden;
  transition: max-height 0.4s ease, opacity 0.35s ease;
}

.achv-card.featured .achv-caption {
  max-height: 120px;
  opacity: 1;
}

.achv-card:hover .achv-caption {
  max-height: 120px;
  opacity: 1;
}

/* Trust Strip */
.achv-trust-strip {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

.trust-pill {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  background: linear-gradient(135deg, rgba(79, 189, 176, 0.15), rgba(244, 201, 122, 0.1));
  border: 1px solid rgba(255, 255, 255, 0.15);
  padding: 0.8rem 1.5rem;
  border-radius: 999px;
  transition: all 0.3s ease;
}

.trust-pill:hover {
  transform: translateY(-3px);
  border-color: rgba(244, 201, 122, 0.5);
  background: linear-gradient(135deg, rgba(79, 189, 176, 0.25), rgba(244, 201, 122, 0.18));
}

.trust-icon {
  font-size: 1.2rem;
}

.trust-text {
  color: #fff;
  font-size: 0.85rem;
  font-weight: 600;
  white-space: nowrap;
}

/* Responsive */
@media (max-width: 968px) {
  .achv-grid {
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: 240px;
  }

  .achv-card.featured {
    grid-column: span 2;
    grid-row: span 1;
    min-height: 320px;
  }

  .achv-caption {
    max-height: 120px;
    opacity: 1;
  }
}

@media (max-width: 640px) {
  .achv-grid {
    grid-template-columns: 1fr;
    grid-auto-rows: 260px;
  }

  .achv-card.featured {
    grid-column: span 1;
    grid-row: span 1;
    min-height: 300px;
  }

  .achv-title {
    font-size: 1rem;
  }

  .achv-card.featured .achv-title {
    font-size: 1.3rem;
  }

  .trust-pill {
    padding: 0.65rem 1.1rem;
  }

  .trust-text {
    font-size: 0.8rem;
  }
}
</style>
