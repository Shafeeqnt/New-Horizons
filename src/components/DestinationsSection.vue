<template>
  <section id="destinations" class="section">
    <div class="container">
      <div class="section-header">
        <span class="subtitle">Explore Kerala</span>
        <h2>Top <span class="text-gradient">Destinations</span></h2>
        <p class="text-muted">Where adventure meets serenity and every bite is a delight</p>
      </div>
      
      <div class="destinations-grid">
        <div v-for="(dest, index) in destinations" :key="index" class="destination-card" :style="{ '--delay': index * 0.1 + 's' }">
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
    </div>
  </section>
</template>

<script setup>
import munnarImg from '../assets/images/munnar.png'
import alleppeyImg from '../assets/images/alleppey.png'

const destinations = [
  {
    name: 'Munnar',
    tag: 'Hill Station',
    description: 'A breathtaking hill station with tea plantations, misty valleys, and waterfalls.',
    image: munnarImg
  },
  {
    name: 'Alleppey',
    tag: 'Backwaters',
    description: 'Famous for tranquil backwaters and luxurious houseboat cruises.',
    image: alleppeyImg
  },
  {
    name: 'Kochi',
    tag: 'Heritage City',
    description: 'A vibrant port city blending colonial charm, historic forts, and spice markets.',
    image: 'https://images.unsplash.com/photo-1602216056096-3b40cc0c9944?w=800&q=80'
  },
  {
    name: 'Thekkady',
    tag: 'Wildlife',
    description: 'Home to Periyar Wildlife Sanctuary offering boat safaris and elephant sightings.',
    image: 'https://images.unsplash.com/photo-1564760055775-d63b17a55c44?w=800&q=80'
  },
  {
    name: 'Kovalam',
    tag: 'Beach Paradise',
    description: 'A paradise for beach lovers with golden sands and Ayurvedic retreats.',
    image: 'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?w=800&q=80'
  },
  {
    name: 'Wayanad',
    tag: 'Nature Haven',
    description: 'A nature lover\'s haven with caves, waterfalls, and wildlife sanctuaries.',
    image: 'https://images.unsplash.com/photo-1433086966358-54859d0ed716?w=800&q=80'
  },
  {
    name: 'Kozhikode',
    tag: 'Food Capital',
    description: 'Near Wayanad, renowned for Malabar cuisine including biryanis and seafood delicacies.',
    image: 'https://images.unsplash.com/photo-1596797038530-2c107229654b?w=800&q=80'
  },
  {
    name: 'Varkala',
    tag: 'Cliffside Beach',
    description: 'Known for stunning cliffs, pristine beaches, and spiritual significance.',
    image: 'https://images.unsplash.com/photo-1519046904884-53103b34b206?w=800&q=80'
  }
]
</script>

<style scoped>
.destinations-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
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
</style>
