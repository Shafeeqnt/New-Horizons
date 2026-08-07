<template>
  <section id="packages" class="section">
    <div class="container">
      <div class="section-header">
        <span class="subtitle">Curated Journeys</span>
        <h2>Tour <span class="text-gradient">Packages</span></h2>
        <p class="text-muted">Thoughtfully designed itineraries for unforgettable experiences</p>
      </div>
      
      <div class="packages-grid">
        <div v-for="(pkg, index) in packages" :key="index" class="package-card" :class="{ 'package-featured': pkg.featured }">
          <div class="package-header" :style="{ background: pkg.gradient }">
            <span class="package-duration">{{ pkg.duration }}</span>
            <h3 class="package-name">{{ pkg.name }}</h3>
            <p class="package-tagline">{{ pkg.tagline }}</p>
          </div>
          
          <div class="package-content">
            <div class="package-itinerary">
              <div v-for="(day, dIndex) in pkg.itinerary" :key="dIndex" class="itinerary-day">
                <div class="day-marker">
                  <span class="day-number">{{ day.day }}</span>
                </div>
                <div class="day-content">
                  <span class="day-title">{{ day.title }}</span>
                  <p class="day-activities">{{ day.activities }}</p>
                </div>
              </div>
            </div>
            
            <div class="package-addons" v-if="pkg.addons.length">
              <span class="addons-label">Customizable Add-ons:</span>
              <div class="addons-list">
                <span v-for="(addon, aIndex) in pkg.addons" :key="aIndex" class="addon-tag">{{ addon }}</span>
              </div>
            </div>
            
            <a href="#contact" class="btn btn-primary package-cta">Get Quote</a>
          </div>
          
          <div v-if="pkg.featured" class="package-ribbon">Most Popular</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const packages = [
  {
    name: 'Wayanad Explorer',
    duration: '3 Days',
    tagline: 'Nature, Heritage & Adventure',
    gradient: 'linear-gradient(135deg, #0b8a6f 0%, #066e58 100%)',
    featured: false,
    itinerary: [
      { day: 'Day 1', title: 'Calicut Arrival', activities: 'Pickup, Planetarium, beach exploration, local food, night stay' },
      { day: 'Day 2', title: 'Heritage & Resort', activities: 'Drive to Wayanad, En-ooru heritage village, resort check-in, Banasura Sagar Dam' },
      { day: 'Day 3', title: 'Trek & Tea', activities: 'Banasura hills or Chembra peak trek, tea plantation visit, drop off' }
    ],
    addons: ['Body massage', 'Edakkal Cave', 'Soochipara waterfalls', 'Kayaking', 'Glass bridge', 'Zipline', 'Muthanga forest']
  },
  {
    name: 'Kerala Grand Tour',
    duration: '4 Days',
    tagline: 'Alappuzha • Munnar • Thekkady',
    gradient: 'linear-gradient(135deg, #d4af37 0%, #f4d03f 100%)',
    featured: true,
    itinerary: [
      { day: 'Day 1', title: 'Kochi to Alappuzha', activities: 'Pickup at Kochi, island beach, drive to Alappuzha, houseboat experience' },
      { day: 'Day 2', title: 'Munnar Mountains', activities: 'Houseboat checkout, scenic drive to Munnar, resort check-in' },
      { day: 'Day 3', title: 'Munnar & Thekkady', activities: 'Kolukkumalai, Tiger Nose viewpoint, Eravikulam National Park, drive to Thekkady' },
      { day: 'Day 4', title: 'Wildlife & Culture', activities: 'Periyar Tiger Reserve, Kathakali & Kalari shows, Spice Garden visit, drop off' }
    ],
    addons: ['Elephant ride', 'Kochi Jewish Town', 'Massage at Thekkady', 'Vagamon paragliding', 'Sunset cruise']
  },
  {
    name: 'Trivandrum Escape',
    duration: '2 Days',
    tagline: 'Coastal Paradise',
    gradient: 'linear-gradient(135deg, #e8925e 0%, #d67b44 100%)',
    featured: false,
    itinerary: [
      { day: 'Day 1', title: 'TVM to Varkala', activities: 'Pickup TVM, SPS Temple, Kovalam Beach, drive to Varkala, sunset at cliff, resort check-in' },
      { day: 'Day 2', title: 'Beaches & Beyond', activities: 'Sunrise view, black sand beach, Jatayu Earth Center with cable car ride, drop off' }
    ],
    addons: ['Paragliding', 'Surfing', 'Munroe or Poovar islands', 'Body massage']
  }
]
</script>

<style scoped>
.packages-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(380px, 100%), 1fr));
  gap: 2.5rem;
  align-items: start;
}

.package-card {
  position: relative;
  background: var(--color-white);
  border-radius: var(--radius-xl);
  overflow: hidden;
  box-shadow: var(--shadow-lg);
  transition: all var(--transition-smooth);
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.package-card:hover {
  transform: translateY(-12px) scale(1.02);
  box-shadow: var(--shadow-xl);
}

.package-featured {
  border: 2px solid var(--color-gold);
  transform: scale(1.05);
  box-shadow: var(--shadow-xl), var(--shadow-glow-gold);
}

.package-featured:hover {
  transform: scale(1.05) translateY(-12px);
  box-shadow: var(--shadow-xl), var(--shadow-glow-gold);
}

.package-ribbon {
  position: absolute;
  top: 20px;
  right: -35px;
  background: var(--color-gold);
  color: var(--color-dark);
  padding: 0.4rem 3rem;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  transform: rotate(45deg);
}

.package-header {
  padding: 2.5rem;
  color: var(--color-white);
  text-align: center;
  position: relative;
  overflow: hidden;
}

.package-header::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(0,0,0,0.1) 0%, rgba(0,0,0,0.3) 100%);
  z-index: 1;
}

.package-header > * {
  position: relative;
  z-index: 2;
}

.package-duration {
  display: inline-block;
  background: rgba(255, 255, 255, 0.2);
  padding: 0.25rem 1rem;
  border-radius: var(--radius-full);
  font-size: 0.8rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
}

.package-name {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: var(--color-white);
}

.package-tagline {
  font-size: 0.9rem;
  opacity: 0.9;
  margin: 0;
}

.package-content {
  padding: 2rem;
}

.package-itinerary {
  margin-bottom: 1.5rem;
}

.itinerary-day {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid var(--color-light-secondary);
}

.itinerary-day:last-child {
  border-bottom: none;
  margin-bottom: 0;
}

.day-marker {
  flex-shrink: 0;
}

.day-number {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 28px;
  height: 28px;
  background: var(--color-primary);
  color: var(--color-white);
  border-radius: 50%;
  font-size: 0.7rem;
  font-weight: 700;
}

.day-content {
  flex: 1;
}

.day-title {
  display: block;
  font-weight: 600;
  color: var(--color-dark);
  margin-bottom: 0.25rem;
}

.day-activities {
  font-size: 0.85rem;
  color: var(--color-text-muted);
  margin: 0;
  line-height: 1.5;
}

.package-addons {
  margin-bottom: 1.5rem;
}

.addons-label {
  display: block;
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--color-dark);
  margin-bottom: 0.5rem;
}

.addons-list {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.addon-tag {
  background: var(--color-light);
  color: var(--color-text);
  padding: 0.25rem 0.75rem;
  border-radius: var(--radius-full);
  font-size: 0.75rem;
}

.package-cta {
  width: 100%;
  text-align: center;
}

@media (max-width: 768px) {
  .packages-grid {
    gap: 2rem;
  }

  .package-featured {
    transform: none;
  }

  .package-featured:hover {
    transform: translateY(-12px);
  }

  .package-header {
    padding: 2rem;
  }

  .package-content {
    padding: 1.5rem;
  }
}

@media (max-width: 480px) {
  .package-header {
    padding: 1.75rem 1.5rem;
  }

  .package-name {
    font-size: 1.25rem;
  }

  .package-content {
    padding: 1.25rem;
  }

  .itinerary-day {
    gap: 0.75rem;
  }

  .package-ribbon {
    top: 14px;
    right: -32px;
    padding: 0.35rem 2.5rem;
    font-size: 0.7rem;
  }
}
</style>
