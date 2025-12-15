<template>
  <section class="section section-dark videos-section">
    <div class="container">
      <div class="section-header">
        <span class="subtitle">Visual Journey</span>
        <h2>Experience <span class="text-gradient">Kerala</span></h2>
        <p class="text-muted">Immerse yourself in the beauty of God's Own Country</p>
      </div>
      
      <div class="videos-grid">
        <div v-for="(video, index) in videos" :key="index" class="video-card">
          <div class="video-wrapper">
            <video 
              :ref="el => videoRefs[index] = el"
              class="video-player"
              autoplay
              loop
              muted
              playsinline
              @mouseenter="unmuteVideo(index)"
              @mouseleave="muteVideo(index)"
            >
              <source :src="video.src" type="video/mp4" />
              Your browser does not support the video tag.
            </video>
            <div class="video-sound-hint" :class="{ 'hidden': unmutedIndex === index }">
              <span>🔊 Hover for sound</span>
            </div>
          </div>
          <div class="video-info">
            <h3 class="video-title">{{ video.title }}</h3>
            <p class="video-desc">{{ video.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const videoRefs = ref([])
const unmutedIndex = ref(null)

// Using high-quality free videos from Pexels
const videos = [
  {
    title: 'Kerala: God\'s Own Country',
    description: 'A visual journey through the stunning backwaters, lush landscapes, and serene beauty of Kerala.',
    src: 'https://videos.pexels.com/video-files/3571264/3571264-uhd_2560_1440_30fps.mp4'
  },
  {
    title: 'Tropical Paradise & Wellness',
    description: 'Discover peaceful nature retreats and the healing environments that make Kerala a wellness destination.',
    src: 'https://videos.pexels.com/video-files/857251/857251-hd_1920_1080_25fps.mp4'
  }
]

const unmuteVideo = (index) => {
  if (videoRefs.value[index]) {
    videoRefs.value[index].muted = false
    unmutedIndex.value = index
  }
}

const muteVideo = (index) => {
  if (videoRefs.value[index]) {
    videoRefs.value[index].muted = true
    unmutedIndex.value = null
  }
}
</script>

<style scoped>
.videos-section {
  background: linear-gradient(180deg, #0d1b2a 0%, #1b263b 50%, #0d1b2a 100%);
}

.videos-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
  gap: 3rem;
}

.video-card {
  border-radius: var(--radius-lg);
  overflow: hidden;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all var(--transition-base);
}

.video-card:hover {
  border-color: rgba(11, 138, 111, 0.5);
  box-shadow: 0 20px 50px rgba(11, 138, 111, 0.2);
}

.video-wrapper {
  position: relative;
  aspect-ratio: 16/9;
  overflow: hidden;
  background: #000;
}

.video-player {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.video-sound-hint {
  position: absolute;
  bottom: 1rem;
  right: 1rem;
  background: rgba(0, 0, 0, 0.7);
  color: var(--color-white);
  padding: 0.5rem 1rem;
  border-radius: var(--radius-full);
  font-size: 0.8rem;
  transition: opacity var(--transition-fast);
}

.video-sound-hint.hidden {
  opacity: 0;
}

.video-info {
  padding: 1.5rem 2rem;
}

.video-title {
  font-size: 1.25rem;
  margin-bottom: 0.5rem;
  color: var(--color-white);
}

.video-desc {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.7);
  margin: 0;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .videos-grid {
    grid-template-columns: 1fr;
  }
}
</style>
