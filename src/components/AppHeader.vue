<template>
  <header class="header" :class="{ scrolled: isScrolled }">
    <div class="container">
      <a href="#" class="logo">
        <img :src="logoUrl" />
        <div>
          <span class="name">New Horizons</span>
          <span class="tagline">Healing • Ayurveda • Travel</span>
        </div>
      </a>

      <nav :class="{ open: isMobileMenuOpen }">
        <a href="#why">Why Kerala</a>
        <a href="#destinations">Destinations</a>
        <a href="#packages">Packages</a>
        <a href="#contact" class="btn btn-gold">Call Now</a>
      </nav>

      <button class="menu-btn" @click="toggleMobileMenu">
        ☰
      </button>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logoUrl from '../assets/logo.jpg'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
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
  padding: -0.4rem 2rem;
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
  border-radius: 8px;
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
  background: none;
  font-size: 1.5rem;
}

@media (max-width: 900px) {
  nav {
    position: fixed;
    top: 0;
    right: -100%;
    height: 100vh;
    width: 80%;
    background: #fff;
    flex-direction: column;
    justify-content: center;
    transition: right 0.3s ease;
  }

  nav.open {
    right: 0;
  }

  .menu-btn {
    display: block;
  }
}
</style>
