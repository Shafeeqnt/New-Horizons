<template>
  <section id="contact" class="section section-dark contact-section">
    <div class="container">
      <div class="contact-wrapper">
        <div class="contact-info">
          <span class="subtitle">Get In Touch</span>
          <h2>Let's Plan Your <span class="text-gradient">Journey</span></h2>
          <p>As a professional tour operator based in Kerala, we offer personalized travel packages tailored to your tastes and preferences, ensuring comfort, enrichment, and seamless integration of medical appointments.</p>
          
          <div class="contact-details">
            <div class="contact-item">
              <div class="contact-icon">📞</div>
              <div>
                <span class="contact-label">Call Us</span>
                <a href="tel:+919074477365" class="contact-value">+91 9074 477 365</a>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">💬</div>
              <div>
                <span class="contact-label">WhatsApp</span>
                <a href="https://wa.me/919074477365?text=Hi!%20I'm%20interested%20in%20your%20health%20tourism%20services." target="_blank" class="contact-value whatsapp-link">Chat with us on WhatsApp</a>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">📍</div>
              <div>
                <span class="contact-label">Visit Us</span>
                <span class="contact-value">Room No 14/1954, City Tower<br>Manjeri 676121, Kerala, India</span>
              </div>
            </div>
            <div class="contact-item footer-brand-item">
              <div class="footer-brand">
                <img :src="logoUrl" alt="New Horizons" class="footer-logo" />
                <div class="footer-brand-text">
                  <span class="footer-name">New Horizons</span>
                  <span class="footer-tagline">Where Healing Meets Paradise</span>
                </div>
                <p class="footer-desc">
                  Premium international health tourism services in Kerala, India. Experience world-class healthcare, authentic Ayurveda, and breathtaking destinations.
                </p>
              </div>
            </div>
          </div>
          
          <div class="services-list">
            <h4>On-Demand Services</h4>
            <div class="services-tags">
              <span class="service-tag">Dedicated travel guide</span>
              <span class="service-tag">Baby care</span>
              <span class="service-tag">Food tour with guide</span>
              <span class="service-tag">Trekking guide</span>
              <span class="service-tag">Tent & sleeping bag</span>
              <span class="service-tag">Special occasions</span>
              <span class="service-tag">Accessibility support</span>
            </div>
          </div>
        </div>
        
        <div class="contact-form-wrapper glass-card">
          <!-- Success Message -->
          <div v-if="isSubmitted" class="success-message">
            <div class="success-icon">✅</div>
            <h3>Inquiry Sent Successfully!</h3>
            <p>Thank you, <strong>{{ submittedName }}</strong>! We have received your inquiry about <strong>{{ submittedPackage || 'our services' }}</strong>.</p>
            <p class="success-details">Our team will contact you within <strong>24 hours</strong> at:</p>
            <ul class="contact-methods">
              <li>📧 {{ submittedEmail }}</li>
              <li v-if="submittedPhone">📱 {{ submittedPhone }}</li>
            </ul>
            <div class="success-actions">
              <a :href="whatsappUrl" target="_blank" class="btn btn-whatsapp">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
                Chat Now on WhatsApp
              </a>
              <button @click="resetForm" class="btn btn-outline-dark">Send Another Inquiry</button>
            </div>
          </div>

          <!-- Form -->
          <template v-else>
            <h3>Send an Inquiry</h3>
            <form @submit.prevent="handleSubmit" class="contact-form">
              <div class="form-group">
                <label for="name">Full Name</label>
                <input type="text" id="name" v-model="form.name" placeholder="Your name" required />
              </div>
              <div class="form-row">
                <div class="form-group">
                  <label for="email">Email</label>
                  <input type="email" id="email" v-model="form.email" placeholder="your@email.com" required />
                </div>
                <div class="form-group">
                  <label for="phone">Phone</label>
                  <input type="tel" id="phone" v-model="form.phone" placeholder="+1 234 567 890" />
                </div>
              </div>
              <div class="form-group">
                <label for="package">Interested In</label>
                <select id="package" v-model="form.package">
                  <option value="">Select a package or service</option>
                  <option value="Wayanad Explorer (3 Days)">Wayanad Explorer (3 Days)</option>
                  <option value="Kerala Grand Tour (4 Days)">Kerala Grand Tour (4 Days)</option>
                  <option value="Trivandrum Escape (2 Days)">Trivandrum Escape (2 Days)</option>
                  <option value="Chekkadi Tribal Village Stay">Chekkadi Tribal Village Stay</option>
                  <option value="Infinity Caves Adventure">Infinity Caves Adventure</option>
                  <option value="Midnight Wild Hunt Tent Stay">Midnight Wild Hunt Tent Stay</option>
                  <option value="Medical Tourism Package">Medical Tourism Package</option>
                  <option value="Ayurveda Wellness Retreat">Ayurveda Wellness Retreat</option>
                  <option value="Custom Package">Custom Package</option>
                </select>
              </div>
              <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" v-model="form.message" rows="4" placeholder="Tell us about your travel plans, medical needs, or any special requirements..."></textarea>
              </div>
              <button type="submit" class="btn btn-gold btn-submit" :disabled="isSubmitting">
                <template v-if="isSubmitting">
                  <span class="spinner"></span> Sending...
                </template>
                <template v-else>
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="22" y1="2" x2="11" y2="13"></line><polygon points="22 2 15 22 11 13 2 9 22 2"></polygon></svg>
                  Send Inquiry
                </template>
              </button>
            </form>
          </template>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import logoUrl from '../assets/logo.jpg'

const form = ref({
  name: '',
  email: '',
  phone: '',
  package: '',
  message: ''
})

const isSubmitting = ref(false)
const isSubmitted = ref(false)
const submittedName = ref('')
const submittedEmail = ref('')
const submittedPhone = ref('')
const submittedPackage = ref('')

const whatsappUrl = computed(() => {
  const text = `Hi! I'm ${submittedName.value}. I just submitted an inquiry about ${submittedPackage.value || 'your services'}. Looking forward to hearing from you!`
  return `https://wa.me/919074477365?text=${encodeURIComponent(text)}`
})

const handleSubmit = async () => {
  isSubmitting.value = true
  
  // Store submitted values for success message
  submittedName.value = form.value.name
  submittedEmail.value = form.value.email
  submittedPhone.value = form.value.phone
  submittedPackage.value = form.value.package
  
  // Simulate sending (in production, connect to backend/email service)
  // You can integrate with:
  // 1. Web3Forms (free) - https://web3forms.com
  // 2. Formspree - https://formspree.io
  // 3. Your own backend API
  
  try {
    // Example: Send to Web3Forms (uncomment and add your access key)
    // const response = await fetch('https://api.web3forms.com/submit', {
    //   method: 'POST',
    //   headers: { 'Content-Type': 'application/json' },
    //   body: JSON.stringify({
    //     access_key: 'YOUR_WEB3FORMS_KEY',
    //     name: form.value.name,
    //     email: form.value.email,
    //     phone: form.value.phone,
    //     package: form.value.package,
    //     message: form.value.message,
    //     subject: `New Inquiry: ${form.value.package || 'General'} - ${form.value.name}`
    //   })
    // })
    
    // Simulate network delay
    await new Promise(resolve => setTimeout(resolve, 1500))
    
    // Store inquiry in localStorage for demo (in production, this goes to your backend)
    const inquiries = JSON.parse(localStorage.getItem('newHorizonsInquiries') || '[]')
    inquiries.push({
      ...form.value,
      timestamp: new Date().toISOString(),
      id: Date.now()
    })
    localStorage.setItem('newHorizonsInquiries', JSON.stringify(inquiries))
    
    console.log('Inquiry stored:', form.value)
    
    isSubmitted.value = true
    form.value = { name: '', email: '', phone: '', package: '', message: '' }
    
  } catch (error) {
    console.error('Error submitting form:', error)
    alert('There was an error sending your inquiry. Please try again or contact us directly.')
  } finally {
    isSubmitting.value = false
  }
}

const resetForm = () => {
  isSubmitted.value = false
  submittedName.value = ''
  submittedEmail.value = ''
  submittedPhone.value = ''
  submittedPackage.value = ''
}
</script>

<style scoped>
.contact-section {
  background: var(--gradient-dark);
  position: relative;
  overflow: hidden;
}

.contact-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: var(--gradient-premium);
}

.contact-wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.contact-info .subtitle {
  color: var(--color-primary-light);
}

.contact-info h2 {
  margin-bottom: 1rem;
}

.contact-info > p {
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 2rem;
  line-height: 1.8;
}

.contact-details {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.contact-item {
  display: flex;
  gap: 1rem;
  align-items: flex-start;
}

.contact-icon {
  font-size: 1.5rem;
  width: 50px;
  height: 50px;
  background: rgba(11, 138, 111, 0.2);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.contact-label {
  display: block;
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.6);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 0.25rem;
}

.contact-value {
  color: var(--color-white);
  font-size: 1rem;
  line-height: 1.5;
}

a.contact-value:hover {
  color: var(--color-primary-light);
}

.whatsapp-link {
  color: #25D366 !important;
}

.whatsapp-link:hover {
  color: #128C7E !important;
}

.services-list h4 {
  font-family: var(--font-body);
  font-size: 0.9rem;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 0.75rem;
}

.services-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.service-tag {
  background: rgba(255, 255, 255, 0.1);
  color: rgba(255, 255, 255, 0.9);
  padding: 0.4rem 0.8rem;
  border-radius: var(--radius-full);
  font-size: 0.8rem;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.contact-form-wrapper {
  padding: 3rem;
  background: var(--glass-dark-bg);
  backdrop-filter: var(--glass-blur);
  border: 1px solid var(--glass-dark-border);
}

.contact-form-wrapper h3 {
  color: var(--color-white);
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
}

/* Success Message Styles */
.success-message {
  text-align: center;
  padding: 1rem 0;
}

.success-icon {
  font-size: 4rem;
  margin-bottom: 1rem;
}

.success-message h3 {
  color: #25D366;
  margin-bottom: 1rem;
}

.success-message p {
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 0.5rem;
}

.success-details {
  margin-top: 1rem;
}

.contact-methods {
  list-style: none;
  padding: 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: var(--radius-md);
  margin: 1rem 0;
}

.contact-methods li {
  color: var(--color-white);
  padding: 0.5rem 0;
}

.success-actions {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 1.5rem;
}

.btn-whatsapp {
  background: #25D366;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.btn-whatsapp:hover {
  background: #128C7E;
  transform: translateY(-2px);
}

.btn-outline-dark {
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: var(--color-white);
}

.btn-outline-dark:hover {
  background: rgba(255, 255, 255, 0.1);
}

/* Form Styles */
.form-group {
  margin-bottom: 1.25rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

label {
  display: block;
  font-size: 0.85rem;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 0.5rem;
}

input, select, textarea {
  width: 100%;
  padding: 1rem 1.25rem;
  background: rgba(255, 255, 255, 0.05);
  border: 2px solid rgba(255, 255, 255, 0.1);
  border-radius: var(--radius-md);
  color: var(--color-white);
  font-size: 1rem;
  font-family: var(--font-body);
  transition: all var(--transition-smooth);
}

input::placeholder, textarea::placeholder {
  color: rgba(255, 255, 255, 0.4);
}

input:focus, select:focus, textarea:focus {
  outline: none;
  border-color: var(--color-emerald);
  background: rgba(255, 255, 255, 0.1);
  box-shadow: 0 0 0 4px rgba(16, 185, 129, 0.2), var(--shadow-glow-emerald);
  transform: translateY(-2px);
}

select {
  cursor: pointer;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='white' stroke-width='2'%3E%3Cpolyline points='6 9 12 15 18 9'%3E%3C/polyline%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 1rem center;
}

select option {
  background: var(--color-dark);
  color: var(--color-white);
}

textarea {
  resize: vertical;
  min-height: 100px;
}

.btn-submit {
  width: 100%;
  padding: 1rem;
  font-size: 1rem;
}

.btn-submit:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.spinner {
  display: inline-block;
  width: 18px;
  height: 18px;
  border: 2px solid rgba(0,0,0,0.3);
  border-top-color: var(--color-dark);
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

/* Footer Brand Styles */
.footer-brand-item {
  display: block;
  margin-top: 2rem;
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
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
  margin: 0;
}

@media (max-width: 968px) {
  .contact-wrapper {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .form-row {
    grid-template-columns: 1fr;
  }
}
</style>
