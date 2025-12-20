# Our Story Section - Setup Guide

## Overview
The "Our Story" section has been successfully created and integrated into your landing page, positioned right after the hero section. This section showcases your two founders with an impressive, modern design.

## Current Status
✅ Component created: `src/components/OurStorySection.vue`
✅ Integrated into: `src/App.vue`
✅ Design complete with animations and responsive layout
⏳ Pending: Founder images (placeholders currently in place)

## Features Included

### 1. **Dual Founder Cards**
- Tourism Consultant (The Explorer)
- Healthcare Specialist (The Healer)
- Each card includes:
  - Circular image placeholder
  - Professional badge
  - Stats display
  - Personal story section

### 2. **Visual Elements**
- Animated connection element between founders
- Floating heart icon with "United Vision" text
- Gradient backgrounds
- Hover effects and micro-animations
- Decorative background circles

### 3. **Mission Statement**
- Shared mission section with gradient background
- Three core values with icons
- Rotating decorative elements

## Adding Founder Images

### Step 1: Prepare Your Images
1. Get professional photos of both founders
2. Recommended specifications:
   - Format: JPG or PNG
   - Minimum size: 400x400 pixels
   - Aspect ratio: 1:1 (square)
   - Background: Preferably solid or blurred

### Step 2: Add Images to Project
1. Save the images in: `src/assets/images/`
2. Suggested names:
   - `founder-tourism.jpg` (for the tourism consultant)
   - `founder-healthcare.jpg` (for the healthcare specialist)

### Step 3: Update the Component
Open `src/components/OurStorySection.vue` and make these changes:

#### A. Add imports in the `<script setup>` section:
```vue
<script setup>
import founderTourism from '../assets/images/founder-tourism.jpg'
import founderHealthcare from '../assets/images/founder-healthcare.jpg'
</script>
```

#### B. Replace Founder 1 placeholder (around line 20):
Find this section:
```vue
<div class="founder-image founder-1">
  <!-- Placeholder for founder image - will be added later -->
  <div class="image-placeholder">
    <span class="placeholder-icon">🌍</span>
  </div>
</div>
```

Replace with:
```vue
<div class="founder-image founder-1">
  <img :src="founderTourism" alt="Tourism Consultant - Founder" />
</div>
```

#### C. Replace Founder 2 placeholder (around line 55):
Find this section:
```vue
<div class="founder-image founder-2">
  <!-- Placeholder for founder image - will be added later -->
  <div class="image-placeholder">
    <span class="placeholder-icon">🏥</span>
  </div>
</div>
```

Replace with:
```vue
<div class="founder-image founder-2">
  <img :src="founderHealthcare" alt="Healthcare Specialist - Founder" />
</div>
```

#### D. Add image styling in the `<style scoped>` section:
Add this CSS rule (you can add it after the `.founder-image` rule):
```css
.founder-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
```

## Customization Options

### Update Founder Names
Edit lines around 30 and 65:
```vue
<h3 class="founder-name">Your Founder's Name</h3>
```

### Update Roles
Edit the founder role text:
```vue
<p class="founder-role">Specific Title Here</p>
```

### Update Stats
Modify the statistics to reflect actual numbers:
```vue
<div class="stat-item">
  <span class="stat-value">50+</span>
  <span class="stat-label">Countries Visited</span>
</div>
```

### Update Stories
Edit the founder story paragraphs to include actual biographical information:
```vue
<p class="founder-story">
  Your custom story text here...
</p>
```

### Update Mission Statement
Customize the mission text (around line 85):
```vue
<p class="mission-text">
  Your custom mission statement...
</p>
```

## Design Features

### Animations
- **Pulse effect** on founder images
- **Heartbeat animation** on connection icon
- **Float animation** on decorative elements
- **Hover effects** on all cards
- **Sparkle animation** on mission icon

### Color Scheme
- Primary: `#1f7a6b` (Teal)
- Secondary: `#4fbdb0` (Light Teal)
- Accent: `#f4c97a` (Gold)
- Background: Gradient from `#f8f9fa` to `#f0f7f6`

### Responsive Breakpoints
- Desktop: Full 3-column layout
- Tablet (< 1024px): Stacked layout with horizontal connection
- Mobile (< 768px): Optimized spacing and smaller images

## Testing
After adding images, test the section:
1. Check image loading
2. Verify responsive behavior on different screen sizes
3. Test hover effects
4. Ensure smooth animations

## Support
If you need to adjust any styling or functionality, all the code is in:
`src/components/OurStorySection.vue`

The component is fully self-contained with scoped styles.
