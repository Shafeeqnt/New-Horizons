<template>
  <section id="experiences" class="section section-dark">
    <div class="container">
      <div class="section-header">
        <span class="subtitle">Exclusive Adventures</span>
        <h2>Premium <span class="text-gradient">Experiences</span></h2>
        <p class="text-muted">Handpicked extraordinary adventures for discerning travelers</p>
      </div>
      
      <div class="experiences-showcase">
        <div v-for="(exp, index) in experiences" :key="index" class="experience-card" :class="{ 'featured': index === 0 }">
          <div class="experience-image-wrapper">
            <img :src="exp.image" :alt="exp.title" class="experience-image" />
            <div class="experience-badge">{{ exp.badge }}</div>
          </div>
          <div class="experience-content">
            <h3 class="experience-title">{{ exp.title }}</h3>
            <p class="experience-location">📍 {{ exp.location }}</p>
            <p class="experience-desc">{{ exp.description }}</p>
            <ul class="experience-highlights">
              <li v-for="(highlight, hIndex) in exp.highlights" :key="hIndex">
                <span class="highlight-icon">✦</span> {{ highlight }}
              </li>
            </ul>
            <a href="#contact" class="btn btn-gold experience-cta">Inquire Now</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import chekkadi from '../assets/images/chekkadi.png'
import caves from '../assets/images/caves.png'
import tent from '../assets/images/tent.png'

const experiences = [
  {
    title: 'Chekkadi Tribal Village Stay',
    location: 'Wayanad, Kerala',
    badge: 'Cultural Immersion',
    description: 'Experience authentic tribal life in an enchanting village bordered by forests on three sides and the Kabini River. Witness sustainable rice farming, traditional craftsmanship, and warm hospitality.',
    highlights: [
      'Traditional bamboo craftsmanship workshops',
      'Gandhakasala rice cultivation experience',
      'Forest walks with tribal guides',
      'Authentic local cuisine'
    ],
    image: chekkadi
  },
  {
    title: 'Infinity Caves Adventure Trek',
    location: 'Wonder Caves, Wayanad',
    badge: 'Adventure',
    description: 'Explore hundreds of connected cave systems formed by uniquely shaped boulders. Discover the natural "AC plant" within caves and trek to viewpoints offering panoramic views of Wayanad.',
    highlights: [
      'Unique boulder formations',
      'Natural cool-air caves',
      '700m viewpoint trek',
      'Camping under the stars'
    ],
    image: caves
  },
  {
    title: 'Midnight Wild Hunt Tent Stay',
    location: 'Stingray Tribe Eco Camp, Wayanad',
    badge: 'Wilderness',
    description: 'Sleep in suspended Stingray tents amidst the forest canopy. Wake to wilderness sounds, stargaze at night, and embark on nocturnal wildlife safaris in pristine natural surroundings.',
    highlights: [
      'Unique hanging tent experience',
      'Night safari for wildlife',
      'Campfire under the stars',
      'Leave-no-trace eco experience'
    ],
    image: tent
  }
]
</script>

<style scoped>
.experiences-showcase {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.experience-card {
  background: var(--glass-dark-bg);
  backdrop-filter: var(--glass-blur);
  border: 1px solid var(--glass-dark-border);
  border-radius: var(--radius-xl);
  overflow: hidden;
  transition: all var(--transition-smooth);
}

.experience-card:hover {
  transform: translateY(-12px) scale(1.02);
  border-color: rgba(16, 185, 129, 0.5);
  box-shadow: var(--shadow-xl), var(--shadow-glow-emerald);
  background: rgba(255, 255, 255, 0.08);
}

.experience-card.featured {
  grid-row: span 2;
}

.experience-image-wrapper {
  position: relative;
  height: 280px;
  overflow: hidden;
}

.experience-card.featured .experience-image-wrapper {
  height: 350px;
}

.experience-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform var(--transition-slow);
}

.experience-card:hover .experience-image {
  transform: scale(1.08);
}

.experience-badge {
  position: absolute;
  top: 1rem;
  left: 1rem;
  background: var(--gradient-gold);
  color: var(--color-dark);
  padding: 0.5rem 1rem;
  border-radius: var(--radius-full);
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.experience-content {
  padding: 2rem;
}

.experience-title {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: var(--color-white);
}

.experience-location {
  font-size: 0.9rem;
  color: var(--color-primary-light);
  margin-bottom: 1rem;
}

.experience-desc {
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.95rem;
  line-height: 1.7;
  margin-bottom: 1.5rem;
}

.experience-highlights {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.experience-highlights li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: rgba(255, 255, 255, 0.9);
  font-size: 0.9rem;
}

.highlight-icon {
  color: var(--color-gold);
}

.experience-cta {
  width: 100%;
  text-align: center;
}

@media (max-width: 1200px) {
  .experiences-showcase {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .experience-card.featured {
    grid-row: span 1;
  }
}

@media (max-width: 768px) {
  .experiences-showcase {
    grid-template-columns: 1fr;
  }
}
</style>
