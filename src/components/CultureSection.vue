<template>
  <section class="section culture-section">
    <div class="container">
      <div class="culture-content">
        <div class="culture-text">
          <span class="subtitle">Rich Heritage</span>
          <h2>Kerala's Vibrant <span class="text-gradient">Culture</span></h2>
          <p>Kerala's culture is a vibrant blend of art, festivals, and warm hospitality. Experience ancient art forms, colorful celebrations, and a unique cultural tapestry woven over millennia.</p>
          
          <div class="culture-highlights">
            <div class="culture-item">
              <span class="culture-icon">🎭</span>
              <div>
                <h4>Ancient Art Forms</h4>
                <p>Kathakali, Mohiniyattam, and Theyyam performances</p>
              </div>
            </div>
            <div class="culture-item">
              <span class="culture-icon">🎉</span>
              <div>
                <h4>Vibrant Festivals</h4>
                <p>Onam, Eid, Christmas celebrated together</p>
              </div>
            </div>
            <div class="culture-item">
              <span class="culture-icon">🌿</span>
              <div>
                <h4>Living Traditions</h4>
                <p>Ayurveda, spice cultivation, martial arts</p>
              </div>
            </div>
            <div class="culture-item">
              <span class="culture-icon">🤝</span>
              <div>
                <h4>Warm Hospitality</h4>
                <p>Harmonious blend of Hindu, Muslim, and Christian communities</p>
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
              <div class="food-item">🍛 Beef curry, spicy chicken, mutton porotta</div>
              <div class="food-item">🦐 Fish curry, prawns in coconut gravies</div>
              <div class="food-item">🍌 Kerala Sadya vegetarian feast</div>
              <div class="food-item">🥘 Kozhikode-style biryani</div>
              <div class="food-item">🍘 Banana chips, cutlets, samosas</div>
              <div class="food-item">🥮 Thalasseri chicken & mutton rolls</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.culture-section {
  background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
}

.culture-content {
  display: grid;
  grid-template-columns: 1.2fr 0.8fr;
  gap: 4rem;
  align-items: center;
}

.culture-text .subtitle {
  color: var(--color-primary);
}

.culture-text h2 {
  margin-bottom: 1rem;
}

.culture-text > p {
  color: var(--color-text-muted);
  font-size: 1.1rem;
  margin-bottom: 2rem;
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
}

.culture-icon {
  font-size: 2rem;
  flex-shrink: 0;
}

.culture-item h4 {
  font-family: var(--font-body);
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 0.25rem;
  color: var(--color-dark);
}

.culture-item p {
  font-size: 0.85rem;
  color: var(--color-text-muted);
  margin: 0;
}

.food-card {
  background: var(--color-white);
  border-radius: var(--radius-lg);
  padding: 2.5rem;
  box-shadow: var(--shadow-lg);
  position: relative;
  overflow: hidden;
}

.food-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--gradient-gold);
}

.food-badge {
  display: inline-block;
  background: var(--gradient-gold);
  color: var(--color-dark);
  padding: 0.25rem 1rem;
  border-radius: var(--radius-full);
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.food-card h3 {
  font-size: 1.75rem;
  margin-bottom: 0.5rem;
}

.food-intro {
  font-size: 0.95rem;
  color: var(--color-text-muted);
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
  background: var(--color-light);
  border-radius: var(--radius-md);
  font-size: 0.9rem;
  color: var(--color-dark);
  transition: all var(--transition-fast);
}

.food-item:hover {
  background: var(--color-primary);
  color: var(--color-white);
  transform: translateX(5px);
}

@media (max-width: 968px) {
  .culture-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .culture-highlights {
    grid-template-columns: 1fr;
  }
}
</style>
