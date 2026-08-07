<template>
  <header class="header" :class="{ scrolled: isScrolled }">
    <div class="container">
      <a href="#" class="logo">
        <img :src="logoUrl" />
        <div>
          <span class="name">Cure Kerala</span>
          <span class="tagline">Healing • Ayurveda • Travel</span>
        </div>
      </a>

      <nav :class="{ open: isMobileMenuOpen }">
        <a href="#why" @click="closeMobileMenu">Why Kerala</a>
        <a href="#destinations" @click="closeMobileMenu">Destinations</a>
        <a href="#packages" @click="closeMobileMenu">Packages</a>
        <a href="#contact" class="btn btn-gold" @click="closeMobileMenu">Call Now</a>
      </nav>

      <div v-if="isMobileMenuOpen" class="nav-backdrop" @click="closeMobileMenu"></div>

      <button class="menu-btn" :class="{ active: isMobileMenuOpen }" @click="toggleMobileMenu" aria-label="Toggle menu">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logoUrl from '../assets/cure-kerala-icon.png'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 40
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.header {
  position: fixed;
  inset: 0 0 auto 0;
  padding: 1rem 2rem;
  z-index: 1000;
  transition: all 0.3s ease;
}

.header.scrolled {
  background: rgba(255,255,255,0.92);
  backdrop-filter: blur(14px);
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
}

.container {
  max-width: 1400px;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  display: flex;
  gap: 0.75rem;
  align-items: center;
}

.logo img {
  height: 44px;
  width: 44px;
  object-fit: cover;
  border-radius: 8px;
  flex-shrink: 0;
}

.name {
  font-weight: 700;
  color: #1f7a6b;
}

.tagline {
  font-size: 0.65rem;
  text-transform: uppercase;
  color: #4c5b45;
  padding-left: 10px;
  white-space: nowrap;
}

nav {
  display: flex;
  gap: 2rem;
  align-items: center;
}

nav a {
  font-weight: 500;
  color: #1c2d2a;
}

.header:not(.scrolled) nav a {
  color: #00000077;
}

.menu-btn {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  width: 32px;
  height: 32px;
  padding: 0;
  background: none;
  border: none;
  cursor: pointer;
  z-index: 1001;
}

.menu-btn span {
  display: block;
  width: 100%;
  height: 2px;
  background: #1c2d2a;
  border-radius: 2px;
  transition: all 0.3s ease;
}

.menu-btn.active span:nth-child(1) {
  transform: translateY(7px) rotate(45deg);
}

.menu-btn.active span:nth-child(2) {
  opacity: 0;
}

.menu-btn.active span:nth-child(3) {
  transform: translateY(-7px) rotate(-45deg);
}

.nav-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.4);
  z-index: 999;
}

@media (max-width: 900px) {
  .container {
    padding: 0 0.5rem;
  }

  nav {
    position: fixed;
    top: 0;
    right: -100%;
    height: 100vh;
    width: min(320px, 80%);
    background: #fff;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    overflow-y: auto;
    padding: 2rem 0;
    box-shadow: -8px 0 30px rgba(0, 0, 0, 0.15);
    transition: right 0.3s ease;
    z-index: 1000;
  }

  nav.open {
    right: 0;
  }

  .menu-btn {
    display: flex;
  }
}

@media (max-width: 480px) {
  .header {
    padding: 0.75rem 1rem;
  }

  .logo img {
    height: 36px;
    width: 36px;
  }

  .name {
    font-size: 0.95rem;
  }

  .tagline {
    display: none;
  }
}
</style>
