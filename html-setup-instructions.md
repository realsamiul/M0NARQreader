# HTML Setup Instructions - Production Ready

## 1. Critical: Update EVERY HTML File

Apply these changes to **all** HTML files:
- index.html
- home-2.html, home-3.html
- services-1.html, services-2.html, services-3.html
- about-1.html, about-2.html, about-3.html
- customers.html, pricing.html, contact.html, book-consultation.html
- blog.html, blog-post.html
- legal.html, template pages, etc.

---

## 2. HEAD Section Changes

### A. Replace CSS Link
**Find:**
```html
<link href="https://cdn.prod.website-files.com/.../css/hardware-technology-consulting-template.webflow.shared.93bb2e508.css" rel="stylesheet" type="text/css"/>
```

**Replace with:**
```html
<link href="hardware-technology-consulting-template.webflow.shared.93bb2e508.css" rel="stylesheet" type="text/css"/>
```

### B. Add Mobile Optimizations

**Add this style block AFTER the CSS link:**

```html
<style>
  /* Font smoothing */
  body {
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
  }
  
  /* Split text styling */
  .char {
    display: inline-block;
    transform-origin: bottom center;
    will-change: transform, opacity;
  }
  
  .word {
    display: inline-block;
    white-space: nowrap;
  }
  
  /* Hero images start hidden */
  .hero-bg {
    opacity: 0;
  }
  
  /* Performance optimizations */
  main, .hero-section, .button, .image-fill {
    will-change: transform, opacity;
  }
  
  /* Mobile button sizing - Google standards (48px minimum) */
  @media (max-width: 767px) {
    .button {
      min-height: 48px !important;
      min-width: 48px !important;
      padding: 14px 20px !important;
      font-size: 16px !important; /* Prevents iOS zoom */
    }
    
    .menu-button {
      min-width: 48px !important;
      min-height: 48px !important;
      padding: 12px !important;
    }
    
    /* Form inputs - prevent iOS zoom */
    input, textarea, select {
      font-size: 16px !important;
    }
    
    /* Touch-friendly links */
    a {
      min-height: 44px;
      display: inline-flex;
      align-items: center;
    }
  }
  
  /* Smooth transitions */
  main, .hero-section {
    transition: none;
  }
  
  /* Prevent layout shift */
  img, .image-fill {
    content-visibility: auto;
  }
  
  /* Mobile menu optimizations */
  .navbar-menu {
    -webkit-overflow-scrolling: touch;
  }
</style>
```

### C. Add Viewport Meta (verify it exists)

```html
<meta content="width=device-width, initial-scale=1, maximum-scale=5, user-scalable=yes" name="viewport"/>
```

---

## 3. BODY Section Changes

### A. Remove ALL Webflow Scripts

**Delete these entirely:**
```html
<script src="https://d3e54v103j8qbb.cloudfront.net/js/jquery-3.5.1.min.dc5e7f18c8.js?site=..."></script>
<script src="https://cdn.prod.website-files.com/.../js/webflow.2c9b5007c.js"></script>
<script src="gsap-animations.js"></script> <!-- Remove old file -->
```

### B. Add Master JS (ONLY)

**Before closing `</body>` tag:**

```html
  <!-- Master Animation System -->
  <script type="module" src="master.js"></script>
</body>
</html>
```

---

## 4. Complete Example: index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Hardware - Webflow HTML Website Template</title>
  <meta content="..." name="description">
  <meta content="width=device-width, initial-scale=1, maximum-scale=5, user-scalable=yes" name="viewport">
  
  <!-- LOCAL CSS -->
  <link href="hardware-technology-consulting-template.webflow.shared.93bb2e508.css" rel="stylesheet" type="text/css">
  
  <!-- Icons -->
  <link href="https://cdn.prod.website-files.com/68e870847ab6585e89e03ded/690016b2b45a367a37815563_favicon.png" rel="shortcut icon" type="image/x-icon">
  <link href="https://cdn.prod.website-files.com/68e870847ab6585e89e03ded/690016b743eebae2ac50aeee_webclip.png" rel="apple-touch-icon">
  
  <style>
    body {
      -moz-osx-font-smoothing: grayscale;
      -webkit-font-smoothing: antialiased;
    }
    
    .char {
      display: inline-block;
      transform-origin: bottom center;
      will-change: transform, opacity;
    }
    
    .word {
      display: inline-block;
      white-space: nowrap;
    }
    
    .hero-bg {
      opacity: 0;
    }
    
    main, .hero-section, .button, .image-fill {
      will-change: transform, opacity;
    }
    
    @media (max-width: 767px) {
      .button {
        min-height: 48px !important;
        min-width: 48px !important;
        padding: 14px 20px !important;
        font-size: 16px !important;
      }
      
      .menu-button {
        min-width: 48px !important;
        min-height: 48px !important;
        padding: 12px !important;
      }
      
      input, textarea, select {
        font-size: 16px !important;
      }
      
      a {
        min-height: 44px;
        display: inline-flex;
        align-items: center;
      }
    }
    
    main, .hero-section {
      transition: none;
    }
    
    img, .image-fill {
      content-visibility: auto;
    }
    
    .navbar-menu {
      -webkit-overflow-scrolling: touch;
    }
  </style>
</head>
<body>
  <!-- Navbar -->
  <div class="navbar w-nav">
    <!-- ... navbar content ... -->
  </div>

  <!-- Hero Section -->
  <section class="hero-section">
    <img class="hero-bg" src="..." alt="">
    <div class="hero-1-content">
      <!-- ... hero content ... -->
    </div>
  </section>

  <!-- Main Content -->
  <section class="section">
    <!-- ... -->
  </section>

  <!-- Footer -->
  <section class="footer">
    <!-- ... -->
  </section>

  <!-- ONLY THIS SCRIPT -->
  <script type="module" src="master.js"></script>
</body>
</html>
```

---

## 5. File Structure Verification

```
project-root/
├── index.html
├── home-2.html
├── home-3.html
├── services-1.html
├── services-2.html
├── services-3.html
├── about-1.html
├── about-2.html
├── about-3.html
├── customers.html
├── pricing.html
├── contact.html
├── book-consultation.html
├── blog.html
├── legal.html
├── master.js ⭐ NEW
├── hardware-technology-consulting-template.webflow.shared.93bb2e508.css
├── 68ec2695530c133f73f63d75_DMMono-Medium.ttf
├── 68ec2695fd70f93bb49c7983_BDOGrotesk-VF.ttf
└── 68ec91e6d86f60bfd8c288cd_DMMono-Light.ttf
```

---

## 6. Mobile Testing Checklist

### Chrome DevTools (Open with F12)
1. Click "Toggle device toolbar" (Ctrl+Shift+M)
2. Select "iPhone 12 Pro" or "Pixel 5"
3. Set throttling to "Fast 3G"
4. Test:

#### Smooth Scrolling
- [ ] Scroll feels buttery with momentum
- [ ] No janky/choppy scroll
- [ ] No scroll snapping or stopping
- [ ] Parallax images move smoothly

#### Page Transitions
- [ ] Tap internal links → smooth fade out/in
- [ ] Transition completes in ~500ms
- [ ] Back button works smoothly
- [ ] No flash of unstyled content

#### Hero Entrance
- [ ] Background image fades in
- [ ] Heading letters roll in one by one
- [ ] Buttons fade in after text
- [ ] Badge/dot appears first
- [ ] Total animation < 2 seconds

#### Mobile Menu
- [ ] Menu button is 48x48px minimum
- [ ] Opens smoothly with blur effect
- [ ] Page scales down and blurs
- [ ] Closes on link tap
- [ ] Closes on outside tap
- [ ] Closes on ESC key

#### Button Touch Targets
- [ ] All buttons ≥ 48px height
- [ ] Buttons have 8px spacing between them
- [ ] Tap doesn't trigger iOS zoom
- [ ] Hover effects work (desktop)

#### Scroll Animations
- [ ] Sections fade in smoothly
- [ ] Images scale/fade reveal
- [ ] Gradient lines animate
- [ ] Metrics count up
- [ ] No animation blocking scroll

#### Performance
- [ ] Page loads in < 3 seconds
- [ ] No lag when scrolling
- [ ] Animations are 60fps
- [ ] No memory leaks (DevTools → Performance)

---

## 7. Troubleshooting

### Issue: Scroll feels janky on mobile
**Solution:** In master.js line 21, change:
```javascript
smoothTouch: false,  // Keep this FALSE for native mobile scroll
```

### Issue: Buttons too small on mobile
**Solution:** Verify CSS in `<head>` includes:
```css
@media (max-width: 767px) {
  .button {
    min-height: 48px !important;
    padding: 14px 20px !important;
  }
}
```

### Issue: Page transition too slow
**Solution:** In master.js line 29, decrease:
```javascript
duration: 0.4,  // Was 0.5
```

### Issue: Hero letters too fast/slow
**Solution:** In master.js line 33, adjust:
```javascript
stagger: 0.02,  // Lower = faster (0.015-0.04)
```

### Issue: Menu doesn't blur page
**Solution:** Check if `.navbar-menu` has proper class. Inspect element to verify.

### Issue: iOS zoom when tapping inputs
**Solution:** Add to all `<input>` and `<textarea>`:
```html
<input ... style="font-size: 16px !important;">
```

---

## 8. Performance Optimization

### A. Preconnect to CDNs
Add to `<head>`:
```html
<link rel="preconnect" href="https://cdn.jsdelivr.net">
<link rel="preconnect" href="https://cdn.prod.website-files.com">
```

### B. Lazy load images below fold
For images NOT in hero:
```html
<img src="..." loading="lazy" alt="...">
```

### C. Reduce motion for accessibility
Add to `<head>` style block:
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 9. Customization

In `master.js`, adjust these values:

```javascript
const CONFIG = {
  lenis: {
    duration: 1.0,        // Scroll speed (0.8 = faster, 1.2 = slower)
    wheelMultiplier: 0.8, // Desktop scroll distance
    touchMultiplier: 1.5, // Mobile scroll distance
  },
  pageTransition: {
    duration: 0.5,        // Page fade speed (0.3-0.8)
  },
  heroEntrance: {
    stagger: 0.025,       // Letter delay (0.015-0.04)
    duration: 1.0,        // Overall hero speed
  },
};
```

---

## 10. Going Live

### Before Deploy:
1. ✅ Test on real iPhone/Android device
2. ✅ Test on slow 3G connection
3. ✅ Run Lighthouse audit (score > 90)
4. ✅ Check all pages load correctly
5. ✅ Verify buttons are touch-friendly
6. ✅ Test landscape orientation

### Lighthouse Score Targets:
- **Performance:** > 90
- **Accessibility:** > 95
- **Best Practices:** > 90
- **SEO:** > 95

---

## 11. Quick Start Commands

```bash
# 1. Create master.js from artifact
# 2. Update all HTML files as above
# 3. Test locally:
python -m http.server 8000
# or
npx serve

# 4. Open browser:
http://localhost:8000
```

---

## Need Help?

Common issues and fixes are in **Section 7: Troubleshooting** above. 

The site should feel like **butter** on mobile - smooth, fast, and delightful. Every animation serves a purpose and never blocks user interaction.

🚀 **Performance First. Mobile First. Buttery Smooth Always.**