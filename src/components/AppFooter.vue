<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-brand">
          <img :src="logoUrl" alt="Cure Kerala" class="footer-logo" />
          <div class="footer-brand-text">
            <span class="footer-name">Cure Kerala</span>
            <span class="footer-tagline">Where Healing Meets Paradise</span>
          </div>
          <p class="footer-desc">
            Premium international health tourism services in Kerala, India. Experience world-class healthcare, authentic Ayurveda, and breathtaking destinations.
          </p>
        </div>
        
        <div class="footer-links">
          <h4>Quick Links</h4>
          <a href="#why-kerala">Why Kerala</a>
          <a href="#destinations">Destinations</a>
          <a href="#experiences">Experiences</a>
          <a href="#packages">Packages</a>
          <a href="#contact">Contact</a>
        </div>
        
        <div class="footer-links">
          <h4>Services</h4>
          <a href="#packages">Medical Tourism</a>
          <a href="#packages">Ayurveda Retreats</a>
          <a href="#packages">Tour Packages</a>
          <a href="#experiences">Adventure Tours</a>
          <a href="#contact">Custom Packages</a>
        </div>
        
        <div class="footer-contact">
          <h4>Contact Us</h4>
          <p>📍 Room No 14/1954, City Tower<br>Manjeri 676121, Kerala, India</p>
          <p>📞 <a href="tel:+919074477365">+91 9074 477 365</a></p>
          <div class="footer-partners">
            <span>In association with:</span>
            <span class="partner">HealthTech</span>
            <span class="partner">Meditation & Yoga Center</span>
          </div>
        </div>
      </div>
      
      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} Cure Kerala. All rights reserved.</p>
        <p class="footer-made">Made with ❤️ for travelers seeking healing and paradise</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import logoUrl from '../assets/cure-kerala-icon.png'

const currentYear = new Date().getFullYear()
</script>

<style scoped>
.footer {
  background: var(--gradient-dark);
  color: var(--color-white);
  padding: var(--space-xl) var(--space-md) var(--space-md);
}

.footer-content {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr 1.2fr;
  gap: 3rem;
  margin-bottom: 3rem;
  padding-bottom: 3rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-brand {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.footer-logo {
  width: 60px;
  height: auto;
  border-radius: 8px;
}

.footer-brand-text {
  display: flex;
  flex-direction: column;
}

.footer-name {
  font-family: var(--font-heading);
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--color-white);
}

.footer-tagline {
  font-size: 0.8rem;
  color: var(--color-accent);
}

.footer-desc {
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.7;
}

.footer-links h4,
.footer-contact h4 {
  font-family: var(--font-body);
  font-size: 1rem;
  font-weight: 600;
  color: var(--color-white);
  margin-bottom: 1.25rem;
}

.footer-links {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.footer-links a {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
  transition: color var(--transition-fast);
}

.footer-links a:hover {
  color: var(--color-primary-light);
}

.footer-contact p {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
  margin-bottom: 0.75rem;
  line-height: 1.6;
}

.footer-contact a {
  color: var(--color-primary-light);
}

.footer-contact a:hover {
  color: var(--color-white);
}

.footer-partners {
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.footer-partners span:first-child {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.5);
}

.partner {
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.8);
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.footer-bottom p {
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.5);
  margin: 0;
}

.footer-made {
  font-size: 0.8rem !important;
}

@media (max-width: 968px) {
  .footer-content {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
  
  .footer-brand {
    grid-column: span 2;
  }
}

@media (max-width: 600px) {
  .footer-content {
    grid-template-columns: 1fr;
  }
  
  .footer-brand {
    grid-column: span 1;
  }
  
  .footer-bottom {
    flex-direction: column;
    text-align: center;
  }
}
</style>
