# LiliCAD Website Agents

Custom agent definitions for working on the LiliCAD static website. These agents help with common tasks and ensure consistency when maintaining the site.

## Available Agents

### 1. Update Version Agent

**Trigger**: When updating the LiliCAD app version and download links

**Tasks**:
- Locate all version references in index.html (currently v0.1.1)
- Update download URLs for all platforms (Windows, macOS, Linux)
- Verify GitHub release URLs are valid
- Check that version numbers are consistent across all three download links
- Update any version references in README.md if needed

**Usage**: "Update LiliCAD version to v0.1.2" or "Update download links to latest release"

---

### 2. Image Optimization Agent

**Trigger**: When adding or optimizing images

**Tasks**:
- Check image file sizes in img/ directory
- Suggest WebP conversions for better compression
- Verify images are appropriately sized for web (not unnecessarily large)
- Check that carousel images maintain consistent aspect ratios
- Ensure alt text is present and descriptive for all images
- Verify retina/high-DPI considerations

**Usage**: "Optimize images" or "Add new screenshot to carousel"

---

### 3. Accessibility Audit Agent

**Trigger**: When reviewing accessibility compliance

**Tasks**:
- Check all images have appropriate alt text
- Verify ARIA labels are present on interactive elements
- Ensure semantic HTML structure is maintained
- Check color contrast ratios meet WCAG AA standards
- Verify keyboard navigation works for slider and carousel
- Test that prefers-reduced-motion is respected
- Validate focus states are visible

**Usage**: "Run accessibility audit" or "Check ARIA labels"

---

### 4. Content Update Agent

**Trigger**: When updating website copy or content

**Tasks**:
- Maintain consistent tone (technical but approachable)
- Ensure feature descriptions match actual app capabilities
- Check that all external links are valid
- Verify email addresses and contact information
- Maintain consistent terminology (e.g., "STL inspection" vs "STL viewing")
- Update meta descriptions if hero/subtitle changes

**Usage**: "Update feature descriptions" or "Refresh website copy"

---

### 5. Responsive Design Tester

**Trigger**: When testing or fixing responsive layout issues

**Tasks**:
- Check CSS breakpoints (particularly @media (max-width: 720px))
- Verify clamp() functions scale properly across viewport sizes
- Test hero heading layout on mobile (switches to column)
- Ensure slider grip size is appropriate on touch devices
- Check download grid responsiveness
- Verify font sizes are readable on small screens

**Usage**: "Test responsive design" or "Fix mobile layout"

---

### 6. Performance Optimizer Agent

**Trigger**: When optimizing site performance

**Tasks**:
- Check that fonts use font-display: swap
- Verify no layout shift issues (CLS)
- Ensure images are lazy-loaded if needed
- Check that external CDN resources (Bootstrap, Analytics) are loaded efficiently
- Verify CSS is minified for production
- Check for unused CSS rules
- Test page load time

**Usage**: "Optimize performance" or "Reduce page load time"

---

### 7. SEO Optimizer Agent

**Trigger**: When improving search engine optimization

**Tasks**:
- Verify meta title is descriptive (currently "LiliCAD · Precision STL Viewer")
- Add/update meta description if missing
- Check Open Graph tags for social media sharing
- Verify canonical URL structure
- Ensure heading hierarchy is logical (h1 → h2)
- Check that content is crawlable
- Verify robots.txt if needed

**Usage**: "Improve SEO" or "Add meta tags"

---

### 8. Deploy Checker Agent

**Trigger**: Before deploying changes to production

**Tasks**:
- Verify CNAME file points to correct domain (lilicad.com)
- Check that all asset paths are relative (no localhost references)
- Ensure Google Analytics ID is correct (G-0V8WSD7C3S)
- Verify download links point to production releases (not test/dev)
- Check that no debug code or console.log statements remain
- Validate HTML structure
- Test in multiple browsers if major changes

**Usage**: "Pre-deployment check" or "Verify production config"

---

### 9. Analytics Review Agent

**Trigger**: When reviewing or updating analytics setup

**Tasks**:
- Verify gtag.js is loaded correctly
- Check tracking ID is valid
- Review tracked events (currently only pageviews)
- Suggest additional event tracking (download clicks, carousel interactions)
- Ensure privacy considerations are met
- Verify analytics script doesn't block rendering

**Usage**: "Review analytics" or "Add download tracking events"

---

### 10. Cross-Browser Test Agent

**Trigger**: When testing browser compatibility

**Tasks**:
- Check backdrop-filter support (fallback for older browsers)
- Verify CSS custom properties work
- Test range input styling across browsers
- Check carousel functionality in Safari, Firefox, Chrome
- Verify font rendering is consistent
- Test on mobile browsers (iOS Safari, Chrome Android)
- Check for any vendor prefix requirements

**Usage**: "Test cross-browser compatibility" or "Check Safari rendering"

---

## Project Context

**Site Type**: Single-page static website
**Framework**: Vanilla HTML/CSS/JS + Bootstrap 5.3.2
**Hosting**: GitHub Pages
**Domain**: lilicad.com
**Purpose**: Landing page for LiliCAD Electron app

## Key Files

- `index.html` - Main and only HTML file (contains all CSS and JS inline)
- `CNAME` - Domain configuration
- `img/` - Screenshots and app icon
- `fonts/` - Self-hosted web fonts
- `favicons/` - Multi-platform favicon assets

## Common Commands

```bash
# Local development server
python -m http.server 8000

# Check for broken links (if using link checker)
npx broken-link-checker http://localhost:8000

# Optimize images (if using imagemin)
npx imagemin img/*.png --out-dir=img/optimized

# Validate HTML
npx html-validate index.html
```

## Style Guidelines

- **Dark theme first**: Site uses dark mode by default
- **Accent color**: #38bdf8 (cyan/sky blue)
- **Typography**: Fira Sans for body, Saira Stencil One for logo
- **Spacing**: Uses clamp() for fluid responsive spacing
- **Animations**: Subtle, respects prefers-reduced-motion
- **Tone**: Professional but approachable, technical but clear

## Deployment Workflow

1. Make changes locally
2. Test with local server
3. Commit to `main` branch
4. GitHub Pages auto-deploys
5. Verify at lilicad.com

## Notes for Agents

- All code is in `index.html` - no separate CSS/JS files
- Bootstrap is only used for the carousel component
- Site is intentionally single-file for simplicity and performance
- Download links point to GitHub Releases in tatstl/lilicad_site repo
- Current version: v0.1.1 (update this when version changes)
