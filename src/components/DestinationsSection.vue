<template>
  <section id="destinations" class="section">
    <div class="container">
      <div class="section-header">
        <span class="subtitle">Explore Kerala</span>
        <h2>Top <span class="text-gradient">Destinations</span></h2>
        <p class="text-muted">Where adventure meets serenity and every bite is a delight</p>
      </div>
      
      <div class="destinations-grid">
        <!-- Always visible destinations -->
        <div 
          v-for="(dest, index) in visibleDestinations" 
          :key="dest.name" 
          class="destination-card" 
          :class="{ 'falling-animation': dest.isNewlyAdded }"
          :style="{ '--delay': index * 0.1 + 's' }"
        >
          <div class="destination-image-wrapper">
            <img :src="dest.image" :alt="dest.name" class="destination-image" loading="lazy" />
            <div class="destination-overlay">
              <span class="destination-tag">{{ dest.tag }}</span>
            </div>
          </div>
          <div class="destination-content">
            <h3 class="destination-name">{{ dest.name }}</h3>
            <p class="destination-desc">{{ dest.description }}</p>
          </div>
        </div>
      </div>

      <!-- Show More Button -->
      <div v-if="!showAll" class="show-more-container">
        <button @click="showMoreDestinations" class="show-more-btn">
          <span class="btn-text">Discover More Destinations</span>
          <span class="btn-icon">✨</span>
          <span class="btn-count">+{{ remainingCount }}</span>
        </button>
        <p class="show-more-hint">Click to reveal more amazing places</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import munnarImg from '../assets/images/munnar.png'
import alleppeyImg from '../assets/images/alleppey.png'

const showAll = ref(false)

const allDestinations = [
  {
    name: 'Munnar',
    tag: 'Hill Station',
    description: 'A breathtaking hill station with tea plantations, misty valleys, and waterfalls.',
    image: munnarImg,
    isNewlyAdded: false
  },
  {
    name: 'Alleppey',
    tag: 'Backwaters',
    description: 'Famous for tranquil backwaters and luxurious houseboat cruises.',
    image: alleppeyImg,
    isNewlyAdded: false
  },
  {
    name: 'Kovalam',
    tag: 'Beach Paradise',
    description: 'A paradise for beach lovers with golden sands and Ayurvedic retreats.',
    image: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?w=800&q=80',
    isNewlyAdded: false
  },
  {
    name: 'Kochi',
    tag: 'Heritage City',
    description: 'A vibrant port city blending colonial charm, historic forts, and spice markets.',
    image: 'https://images.unsplash.com/photo-1602216056096-3b40cc0c9944?w=800&q=80',
    isNewlyAdded: false
  },
  {
    name: 'Thekkady',
    tag: 'Wildlife',
    description: 'Home to Periyar Wildlife Sanctuary offering boat safaris and elephant sightings.',
    image: 'https://images.unsplash.com/photo-1564760055775-d63b17a55c44?w=800&q=80',
    isNewlyAdded: false
  },
  {
    name: 'Wayanad',
    tag: 'Nature Haven',
    description: 'A nature lover\'s haven with caves, waterfalls, and wildlife sanctuaries.',
    image: 'https://images.unsplash.com/photo-1433086966358-54859d0ed716?w=800&q=80',
    isNewlyAdded: false
  },
  {
    name: 'Kozhikode',
    tag: 'Food Capital',
    description: 'Near Wayanad, renowned for Malabar cuisine including biryanis and seafood delicacies.',
    image: 'https://images.unsplash.com/photo-1596797038530-2c107229654b?w=800&q=80',
    isNewlyAdded: false
  },
  {
    name: 'Varkala',
    tag: 'Cliffside Beach',
    description: 'Known for stunning cliffs, pristine beaches, and spiritual significance.',
    image: 'https://images.unsplash.com/photo-1519046904884-53103b34b206?w=800&q=80',
    isNewlyAdded: false
  }
]

const visibleDestinations = computed(() => {
  if (showAll.value) {
    return allDestinations
  }
  return allDestinations.slice(0, 3)
})

const remainingCount = computed(() => {
  return allDestinations.length - 3
})

const showMoreDestinations = () => {
  // Mark new destinations as newly added for animation
  for (let i = 3; i < allDestinations.length; i++) {
    allDestinations[i].isNewlyAdded = true
  }
  showAll.value = true
}
</script>

<style scoped>
.destinations-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(280px, 100%), 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.destination-card {
  background: var(--color-white);
  border-radius: var(--radius-xl);
  overflow: hidden;
  box-shadow: var(--shadow-md);
  transition: all var(--transition-smooth);
  animation: fadeInUp 0.6s ease forwards;
  animation-delay: var(--delay);
  opacity: 0;
}

/* Falling Animation for newly added cards */
.destination-card.falling-animation {
  animation: fallingToss 0.8s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
  opacity: 0;
  transform-origin: top center;
}

@keyframes fallingToss {
  0% {
    opacity: 0;
    transform: translateY(-100px) rotateX(-90deg) rotateZ(-10deg) scale(0.5);
  }
  50% {
    opacity: 0.7;
    transform: translateY(20px) rotateX(10deg) rotateZ(5deg) scale(1.05);
  }
  70% {
    transform: translateY(-10px) rotateX(-5deg) rotateZ(-2deg) scale(0.98);
  }
  100% {
    opacity: 1;
    transform: translateY(0) rotateX(0) rotateZ(0) scale(1);
  }
}

.destination-card:hover {
  transform: translateY(-16px) scale(1.02);
  box-shadow: var(--shadow-xl);
}

.destination-image-wrapper {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.destination-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform var(--transition-slow);
}

.destination-card:hover .destination-image {
  transform: scale(1.1);
}

.destination-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.6) 0%, transparent 50%);
  display: flex;
  align-items: flex-end;
  padding: 1rem;
}

.destination-tag {
  background: var(--gradient-premium);
  color: var(--color-white);
  padding: 0.4rem 1rem;
  border-radius: var(--radius-full);
  font-size: 0.75rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  box-shadow: var(--shadow-sm);
}

.destination-content {
  padding: 1.5rem;
}

.destination-name {
  font-size: 1.25rem;
  margin-bottom: 0.5rem;
  color: var(--color-dark);
}

.destination-desc {
  font-size: 0.9rem;
  color: var(--color-text-muted);
  margin: 0;
  line-height: 1.6;
}

/* Show More Section */
.show-more-container {
  text-align: center;
  margin-top: 3rem;
  padding: 2rem;
  animation: fadeIn 0.8s ease forwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.show-more-btn {
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 1rem;
  background: linear-gradient(135deg, #1f7a6b, #4fbdb0);
  color: white;
  padding: 1.2rem 3rem;
  border: none;
  border-radius: 999px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 10px 30px rgba(31, 122, 107, 0.3);
  overflow: hidden;
}

.show-more-btn::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  transform: translate(-50%, -50%);
  transition: width 0.6s, height 0.6s;
}

.show-more-btn:hover::before {
  width: 300px;
  height: 300px;
}

.show-more-btn:hover {
  transform: translateY(-5px) scale(1.05);
  box-shadow: 0 15px 40px rgba(31, 122, 107, 0.5);
  background: linear-gradient(135deg, #4fbdb0, #1f7a6b);
}

.show-more-btn:active {
  transform: translateY(-2px) scale(1.02);
}

.btn-text {
  position: relative;
  z-index: 2;
}

.btn-icon {
  position: relative;
  z-index: 2;
  font-size: 1.5rem;
  animation: sparkle 2s ease-in-out infinite;
}

@keyframes sparkle {
  0%, 100% {
    transform: scale(1) rotate(0deg);
    opacity: 1;
  }
  50% {
    transform: scale(1.2) rotate(180deg);
    opacity: 0.8;
  }
}

.btn-count {
  position: relative;
  z-index: 2;
  background: rgba(255, 255, 255, 0.25);
  padding: 0.3rem 0.8rem;
  border-radius: 999px;
  font-size: 0.9rem;
  font-weight: 700;
  backdrop-filter: blur(10px);
}

.show-more-hint {
  margin-top: 1rem;
  font-size: 0.95rem;
  color: var(--color-text-muted);
  font-style: italic;
  animation: pulse-text 2s ease-in-out infinite;
}

@keyframes pulse-text {
  0%, 100% {
    opacity: 0.7;
  }
  50% {
    opacity: 1;
  }
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .show-more-btn {
    padding: 1rem 2rem;
    font-size: 1rem;
  }

  .btn-icon {
    font-size: 1.3rem;
  }
}

@media (max-width: 480px) {
  .destinations-grid {
    gap: 1.5rem;
  }

  .show-more-btn {
    padding: 0.9rem 1.5rem;
    font-size: 0.9rem;
    gap: 0.6rem;
  }

  .show-more-hint {
    font-size: 0.85rem;
  }
}
</style>
