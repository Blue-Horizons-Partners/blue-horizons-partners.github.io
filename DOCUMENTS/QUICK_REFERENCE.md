# Minimal Mistakes Theme - Quick Reference
## Blue Horizons Partners Website

---

## Essential Images Summary

### Must-Have Images (Priority 1)
| Image | Dimensions | File | Purpose |
|-------|------------|------|---------|
| **Logo** | 88×88px | `logo.png` | Site header |
| **Bio Photo** | 200×200px | `bio-photo.jpg` | Author sidebar |
| **OG Image** | 1200×630px | `og-image.jpg` | Social sharing |
| **Hero Banner** | 1280×720px | `hero-banner.jpg` | Homepage background |
| **About Header** | 1280×720px | `about-header.jpg` | About page |

### Recommended Images (Priority 2)
| Image | Dimensions | File | Purpose |
|-------|------------|------|---------|
| **Services Header** | 1280×720px | `services-header.jpg` | Services page |
| **Feature 1** | 600×400px | `feature-consulting.jpg` | Homepage feature |
| **Feature 2** | 600×400px | `feature-partnerships.jpg` | Homepage feature |
| **Feature 3** | 600×400px | `feature-innovation.jpg` | Homepage feature |

---

## Quick Install Commands

```bash
# 1. Update Gemfile
cat > Gemfile << 'EOF'
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
gem "jekyll-include-cache", group: :jekyll_plugins
EOF

# 2. Install dependencies
bundle update
bundle install

# 3. Create required directories
mkdir -p _pages assets/images _data

# 4. Test locally
bundle exec jekyll serve
```

---

## Recommended Theme Skins

Try these skins by setting in `_config.yml`:
```yaml
minimal_mistakes_skin: "default"  # Change this value
```

**For Blue Horizons Partners:**
1. **"default"** - Clean, professional (white/gray)
2. **"air"** - Blue theme (matches "horizons")
3. **"contrast"** - Bold, modern look
4. **"aqua"** - Ocean-inspired (matches "blue")

---

## Key Configuration Settings

### In _config.yml:
```yaml
# Theme
remote_theme: "mmistakes/minimal-mistakes@4.28.0"

# Site Identity
title: "Blue Horizons Partners"
subtitle: "Strategic Partnerships & Innovative Solutions"
logo: "/assets/images/logo.png"

# Author
author:
  name: "Blue Horizons Partners"
  avatar: "/assets/images/bio-photo.jpg"
  bio: "Strategic partnerships and innovative solutions"
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:contact@blue-horizons-partners.com"
    - label: "LinkedIn"
      icon: "fab fa-fw fa-linkedin"
      url: "https://www.linkedin.com/company/blue-horizons-partners-1"

# Required Plugins
plugins:
  - jekyll-feed
  - jekyll-include-cache
  - jekyll-seo-tag
  - jekyll-sitemap
```

---

## Page Layout Examples

### Splash Page (Homepage):
```yaml
---
layout: splash
permalink: /
header:
  overlay_image: /assets/images/hero-banner.jpg
  overlay_filter: "0.5"
  actions:
    - label: "Learn More"
      url: "/about/"
excerpt: "Strategic Partnerships & Innovative Solutions"
---
```

### Single Page (About, Services):
```yaml
---
layout: single
title: "About Us"
permalink: /about/
header:
  overlay_image: /assets/images/about-header.jpg
  overlay_filter: "0.5"
author_profile: true
---
```

---

## Navigation Setup

Create `_data/navigation.yml`:
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
```

---

## File Structure After Setup

```
blue-horizons-partners.github.io/
├── _config.yml               # Main configuration
├── Gemfile                   # Ruby dependencies
├── index.md                  # Homepage
├── _data/
│   ├── navigation.yml        # Menu structure
│   └── ui-text.yml          # UI translations
├── _pages/
│   ├── about.md
│   ├── services.md
│   ├── contact.md
│   └── privacy-policy.md
├── _includes/               # Custom includes (optional)
├── _posts/                  # Blog posts (optional)
├── assets/
│   ├── images/
│   │   ├── logo.png
│   │   ├── bio-photo.jpg
│   │   ├── og-image.jpg
│   │   ├── hero-banner.jpg
│   │   ├── about-header.jpg
│   │   └── feature-*.jpg
│   └── css/
│       └── main.scss        # Custom CSS (optional)
└── README.md
```

---

## Useful Links

- 📚 [Full Implementation Plan](./MINIMAL_MISTAKES_IMPLEMENTATION_PLAN.md)
- 🖼️ [Complete Image Requirements](./IMAGE_REQUIREMENTS.md)
- 🔗 [Minimal Mistakes Docs](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
- 🔗 [Theme GitHub Repo](https://github.com/mmistakes/minimal-mistakes)
- 🔗 [Jekyll Documentation](https://jekyllrb.com/docs/)

---

## Common Issues & Solutions

### 1. "Unknown tag 'include_cached'" error
**Solution:** Add to `_config.yml`:
```yaml
plugins:
  - jekyll-include-cache
```
Then run `bundle install`

### 2. Images not showing
**Solution:** 
- Check paths start with `/assets/images/`
- Verify files exist in correct location
- Clear browser cache

### 3. Changes not appearing
**Solution:**
- Restart Jekyll server (`Ctrl+C`, then `bundle exec jekyll serve`)
- For `_config.yml` changes, restart is always required
- Clear browser cache

### 4. Site looks broken
**Solution:**
- Ensure `remote_theme` is set correctly
- Check all required plugins are installed
- Verify `_data/navigation.yml` exists

---

## Testing Checklist

Before deploying:
- [ ] All pages load without errors
- [ ] Navigation menu works
- [ ] Images display correctly
- [ ] Mobile view looks good
- [ ] Links work (internal and external)
- [ ] Social sharing works
- [ ] Contact information is correct
- [ ] Privacy policy is accessible
- [ ] Site loads quickly (< 3 seconds)

---

## Deployment Steps

```bash
# 1. Test locally
bundle exec jekyll serve

# 2. Commit changes
git add .
git commit -m "Migrate to Minimal Mistakes theme"

# 3. Push to GitHub
git push origin main

# 4. Verify deployment
# Visit: https://blue-horizons-partners.github.io
```

GitHub Pages will automatically rebuild your site (takes 1-5 minutes).

---

## Next Actions

1. ✅ Review implementation plan
2. ⬜ Gather/create 5 essential images
3. ⬜ Back up current site
4. ⬜ Update Gemfile and _config.yml
5. ⬜ Create _pages directory and migrate content
6. ⬜ Add images to assets/images/
7. ⬜ Test locally
8. ⬜ Deploy to GitHub Pages

---

## Support

If you run into issues:
1. Check the [full implementation plan](./MINIMAL_MISTAKES_IMPLEMENTATION_PLAN.md)
2. Review [Minimal Mistakes troubleshooting](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
3. Search [GitHub Issues](https://github.com/mmistakes/minimal-mistakes/issues)
4. Check [Jekyll Talk forums](https://talk.jekyllrb.com/)

---

*Last Updated: 2026-07-04*
