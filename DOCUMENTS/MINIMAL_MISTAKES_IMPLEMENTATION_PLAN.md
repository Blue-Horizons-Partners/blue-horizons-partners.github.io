# Minimal Mistakes Theme - Implementation Plan

## Blue Horizons Partners Website

---

## Overview

This plan outlines the migration from the current Minima theme to the Minimal Mistakes Jekyll theme, a professional, feature-rich theme perfect for business websites.

---

## Phase 1: Setup & Installation (Day 1)

### 1.1 Update Dependencies

**Files to modify:** `Gemfile`, `_config.yml`

#### Update Gemfile:

```ruby
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins
```

#### Update \_config.yml:

```yaml
# Theme configuration
remote_theme: "mmistakes/minimal-mistakes@4.28.0"

# Required plugins
plugins:
  - jekyll-feed
  - jekyll-include-cache
  - jekyll-seo-tag
  - jekyll-sitemap
  - jekyll-paginate
```

### 1.2 Run Installation

```bash
bundle update
bundle install
```

---

## Phase 2: Core Configuration (Day 1-2)

### 2.1 Update \_config.yml

Replace current configuration with Minimal Mistakes settings:

```yaml
# Site Settings
title: "Blue Horizons Partners"
subtitle: "Strategic Partnerships & Innovative Solutions"
name: "Blue Horizons Partners"
description: "Blue Horizons Partners is dedicated to helping organizations achieve their goals through strategic partnerships and innovative solutions."
url: "https://blue-horizons-partners.github.io"
baseurl: ""
repository: "Blue-Horizons-Partners/blue-horizons-partners.github.io"
logo: "/assets/images/logo.png" # 88x88px recommended

# Site Skin (color scheme)
minimal_mistakes_skin: "default" # Clean, professional look

# Site Author
author:
  name: "Blue Horizons Partners"
  avatar: "/assets/images/bio-photo.jpg" # 200x200px recommended
  bio: "Strategic partnerships and innovative solutions for your organization"
  location: "United States"
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:contact@blue-horizons-partners.com"
    - label: "LinkedIn"
      icon: "fab fa-fw fa-linkedin"
      url: "https://www.linkedin.com/company/blue-horizons-partners-1"
    - label: "Website"
      icon: "fas fa-fw fa-link"
      url: "https://blue-horizons-partners.github.io"

# Footer Configuration
footer:
  links:
    - label: "LinkedIn"
      icon: "fab fa-fw fa-linkedin"
      url: "https://www.linkedin.com/company/blue-horizons-partners-1"
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:contact@blue-horizons-partners.com"

# Social Sharing
og_image: "/assets/images/og-image.jpg" # 1200x630px recommended
twitter:
  username: # Add if you have Twitter

# Analytics (optional)
analytics:
  provider: false # Set to "google-gtag" if you want Google Analytics

# SEO
social:
  type: Organization
  name: "Blue Horizons Partners"
  links:
    - "https://www.linkedin.com/company/blue-horizons-partners-1"

# Reading Files
include:
  - _pages
  - .htaccess
exclude:
  - "*.sublime-project"
  - "*.sublime-workspace"
  - vendor
  - .asset-cache
  - .bundle
  - .jekyll-assets-cache
  - .sass-cache
  - assets/js/plugins
  - assets/js/_main.js
  - assets/js/vendor
  - Capfile
  - CHANGELOG
  - config
  - Gemfile
  - Gruntfile.js
  - gulpfile.js
  - LICENSE
  - log
  - node_modules
  - package.json
  - package-lock.json
  - Rakefile
  - README
  - tmp

# Defaults
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: true
      comments: false
      share: true
      related: true
  # _pages
  - scope:
      path: "_pages"
      type: pages
    values:
      layout: single
      author_profile: false

# Archives
category_archive:
  type: liquid
  path: /categories/
tag_archive:
  type: liquid
  path: /tags/

# HTML Compression
compress_html:
  clippings: all
  ignore:
    envs: development
```

### 2.2 Create Required Data Files

#### Create `_data/navigation.yml`:

```yaml
main:
  - title: "Home"
    url: /
  - title: "About"
    url: /about/
  - title: "Services"
    url: /services/
  - title: "Contact"
    url: /contact/
  - title: "Privacy Policy"
    url: /privacy-policy/
```

#### Create `_data/ui-text.yml`:

Copy from: https://github.com/mmistakes/minimal-mistakes/blob/master/_data/ui-text.yml
(This provides localized UI text - just use the English section for now)

---

## Phase 3: Page Migration (Day 2-3)

### 3.1 Create \_pages Directory

```bash
mkdir -p _pages
```

### 3.2 Convert Existing Pages

#### Home Page (index.md → \_pages/home.md or keep index.md)

**Option A: Splash Layout (Recommended for business sites)**

```yaml
---
layout: splash
permalink: /
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/hero-banner.jpg
  actions:
    - label: "Learn More"
      url: "/about/"
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
excerpt: "Strategic Partnerships & Innovative Solutions"
intro:
  - excerpt: 'Blue Horizons Partners is dedicated to helping organizations achieve their goals through strategic partnerships and innovative solutions.'
feature_row:
  - image_path: /assets/images/feature-consulting.jpg
    alt: "Strategic Consulting"
    title: "Strategic Consulting"
    excerpt: "Expert guidance for your organization's growth and transformation."
  - image_path: /assets/images/feature-partnerships.jpg
    alt: "Partnership Development"
    title: "Partnership Development"
    excerpt: "Building meaningful relationships that drive mutual success."
  - image_path: /assets/images/feature-innovation.jpg
    alt: "Innovation Solutions"
    title: "Innovation Solutions"
    excerpt: "Cutting-edge approaches to solve complex challenges."
---

{% include feature_row id="intro" type="center" %}

{% include feature_row %}

## Why Choose Blue Horizons Partners?

With years of experience in strategic partnerships and organizational development, we bring a unique perspective to help your business thrive in today's competitive landscape.

[Get Started](/contact/){: .btn .btn--primary .btn--large}
```

**Option B: Home Layout (Blog-style with recent posts)**

```yaml
---
layout: home
author_profile: true
header:
  image: /assets/images/header-home.jpg
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
---
```

#### About Page (about.md → \_pages/about.md)

```yaml
---
layout: single
title: "About Blue Horizons Partners"
permalink: /about/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/about-header.jpg
  caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
author_profile: true
toc: true
toc_label: "On This Page"
toc_icon: "list"
---

## Our Mission

Blue Horizons Partners is dedicated to helping organizations achieve their goals through strategic partnerships and innovative solutions.

## What We Do

We specialize in:
- Strategic consulting and planning
- Partnership development and management
- Innovation and transformation initiatives
- Organizational development

## Our Approach

[Add your content here]

## Our Team

[Add team information]

## Get in Touch

Ready to work with us? [Contact us today](/contact/).
```

#### Create Services Page (\_pages/services.md)

```yaml
---
layout: single
title: "Our Services"
permalink: /services/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/services-header.jpg
author_profile: false
classes: wide
---

## Strategic Consulting

[Add service description]

## Partnership Development

[Add service description]

## Innovation Solutions

[Add service description]

[Contact us](/contact/) to learn how we can help your organization.
```

#### Create Contact Page (\_pages/contact.md)

```yaml
---
layout: single
title: "Contact Us"
permalink: /contact/
header:
  overlay_color: "#333"
author_profile: true
---

We'd love to hear from you. Reach out to discuss how Blue Horizons Partners can help your organization.

## Get in Touch

- **Email:** [contact@blue-horizons-partners.com](mailto:contact@blue-horizons-partners.com)
- **LinkedIn:** [Blue Horizons Partners](https://www.linkedin.com/company/blue-horizons-partners-1)

## Office Information

Blue Horizons Partners
[Address Line 1]
[City, State ZIP]

---

*We typically respond within 24 hours during business days.*
```

#### Update Privacy Policy (privacy-policy.md → \_pages/privacy-policy.md)

```yaml
---
layout: single
title: "Privacy Policy"
permalink: /privacy-policy/
author_profile: false
---
[Keep existing content]
```

---

## Phase 4: Asset Organization (Day 3)

### 4.1 Create Directory Structure

```bash
mkdir -p assets/images
mkdir -p assets/css
mkdir -p assets/js
```

### 4.2 Image Organization

Move/create images in `assets/images/`:

- Logo and branding
- Header/hero images
- Feature images
- Team photos
- Service illustrations

### 4.3 Custom CSS (Optional)

Create `assets/css/main.scss`:

```scss
---
---

@charset "utf-8";

@import "minimal-mistakes/skins/{{ site.minimal_mistakes_skin | default: 'default' }}";
@import "minimal-mistakes";

// Your custom CSS here
.site-title {
  font-size: 1.2em;
}
```

---

## Phase 5: Testing & Refinement (Day 4-5)

### 5.1 Local Testing

```bash
bundle exec jekyll serve
```

Visit http://localhost:4000 and test:

- ✅ All pages load correctly
- ✅ Navigation works
- ✅ Images display properly
- ✅ Mobile responsiveness
- ✅ Links are functional

### 5.2 Refinement Checklist

- [ ] Adjust color scheme (skin selection)
- [ ] Fine-tune typography
- [ ] Optimize images for web
- [ ] Test SEO metadata
- [ ] Verify social sharing
- [ ] Check accessibility

---

## Phase 6: Deployment (Day 5)

### 6.1 GitHub Pages Configuration

1. Ensure `_config.yml` has correct `url` and `repository`
2. Commit all changes
3. Push to GitHub
4. Enable GitHub Pages in repository settings (if not already)

### 6.2 Post-Deployment Verification

- [ ] Visit live site URL
- [ ] Test all pages and links
- [ ] Verify images load
- [ ] Check mobile display
- [ ] Test social sharing previews
- [ ] Validate with Google Search Console (optional)

---

## Optional Enhancements

### Blog Setup

If you want to add a blog:

1. Create `_posts/` directory
2. Add posts with naming: `YYYY-MM-DD-title.md`
3. Use `layout: single` in post front matter
4. Create blog index page

### Contact Form

Consider integrating:

- Formspree
- Netlify Forms (if migrating from GitHub Pages)
- Google Forms embed

### Advanced Features

- Google Analytics integration
- Search functionality
- Comments (Disqus, utterances, or giscus)
- Newsletter signup
- Multiple language support

---

## Theme Skin Selection

**Chosen Skin:** `default`

The **default** skin provides a clean, professional look with:

- Classic white/gray color scheme
- High readability and accessibility
- Professional business appearance
- Works well with any image style
- Wide browser compatibility

This skin is configured in `_config.yml` as:

```yaml
minimal_mistakes_skin: "default"
```

**Note:** If you want to experiment with other skins in the future, options include: "air", "aqua", "contrast", "dark", "dirt", "mint", "neon", "plum", "sunrise"

---

## Troubleshooting

### Common Issues

**Issue:** "Unknown tag 'include_cached'" error
**Solution:** Ensure `jekyll-include-cache` is in Gemfile and plugins list

**Issue:** Images not displaying
**Solution:** Check paths start with `/assets/images/` and files exist

**Issue:** Navigation menu not showing
**Solution:** Verify `_data/navigation.yml` exists and is properly formatted

**Issue:** Styling looks wrong
**Solution:** Clear browser cache, ensure remote_theme is set correctly

---

## Resources

- [Minimal Mistakes Documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
- [Minimal Mistakes GitHub](https://github.com/mmistakes/minimal-mistakes)
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

---

## Timeline Summary

- **Day 1:** Installation & Core Configuration (4-6 hours)
- **Day 2:** Page Migration & Content Setup (4-6 hours)
- **Day 3:** Asset Organization & Customization (3-4 hours)
- **Day 4:** Testing & Refinement (2-3 hours)
- **Day 5:** Deployment & Verification (1-2 hours)

**Total Estimated Time:** 14-21 hours

---

## Next Steps

1. ✅ Review this implementation plan
2. ⬜ Gather/create required images (see IMAGE_REQUIREMENTS.md)
3. ⬜ Back up current site
4. ⬜ Begin Phase 1: Setup & Installation
5. ⬜ Progress through phases sequentially
6. ⬜ Test thoroughly before final deployment

---

_Last Updated: 2026-07-04_
