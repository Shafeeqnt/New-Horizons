<script setup>
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import WhyKerala from './components/WhyKerala.vue'
import DestinationsSection from './components/DestinationsSection.vue'
import ExperiencesSection from './components/ExperiencesSection.vue'
import PackagesSection from './components/PackagesSection.vue'
import VideosSection from './components/VideosSection.vue'
import CultureSection from './components/CultureSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'
</script>

<template>
  <div class="app">
    <AppHeader />
    <main>
      <HeroSection />
      <WhyKerala />
      <DestinationsSection />
      <ExperiencesSection />
      <PackagesSection />
      <VideosSection />
      <CultureSection />
      <ContactSection />
    </main>
    <AppFooter />
  </div>
</template>

<style>
.app {
  width: 100%;
  min-height: 100vh;
}

main {
  width: 100%;
}
</style>
