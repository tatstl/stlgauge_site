# LiliCAD Website

Official landing page for [LiliCAD](https://lilicad.com) - a high-fidelity STL inspection application with precision measurement tools.

## About

This is a single-page static website showcasing LiliCAD, a cross-platform desktop application built with Electron for inspecting and measuring STL files. The website features an interactive light/dark mode comparison slider, a feature showcase carousel, and platform-specific download links.

## Features

- **Interactive Theme Comparison**: Drag-to-compare slider showcasing LiliCAD's light and dark modes
- **Feature Showcase Carousel**: Bootstrap-powered image carousel displaying app capabilities
- **Smart Platform Detection**: Automatically highlights the appropriate download for the visitor's operating system
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **Accessibility**: ARIA labels, semantic HTML, and reduced-motion support
- **Modern UI**: Glassmorphic design with blur effects and smooth transitions

## Project Structure

```
lilicad_site/
├── index.html              # Main landing page
├── CNAME                   # Custom domain configuration (lilicad.com)
├── fonts/                  # Self-hosted web fonts
│   ├── FiraSans-Regular.ttf
│   ├── FiraSans-Bold.ttf
│   └── SairaStencilOne-Regular.ttf
├── img/                    # Images and screenshots
│   ├── icon.png           # App logo
│   ├── dark.png           # Dark mode screenshot
│   ├── light.png          # Light mode screenshot
│   └── carousel/          # Feature showcase images
│       ├── one.png
│       ├── two.png
│       ├── three.png
│       ├── four.png
│       └── five.png
└── favicons/              # Multi-platform favicon assets
    ├── favicon.ico
    ├── favicon.svg
    ├── favicon_*.png
    ├── safari-pinned-tab.svg
    └── site.webmanifest
```

## Technologies

- **HTML5**: Semantic markup
- **CSS3**: Custom properties, grid, flexbox, backdrop-filter
- **JavaScript**: Vanilla ES6+ for interactive components
- **Bootstrap 5.3.2**: Carousel component and utilities
- **Google Analytics**: User analytics (gtag.js)

## Development

### Prerequisites

A modern web browser and a local web server (optional but recommended for testing).

### Local Development

1. Clone this repository:
   ```bash
   git clone https://github.com/tatstl/lilicad_site.git
   cd lilicad_site
   ```

2. Serve the site locally using any static file server:
   ```bash
   # Using Python 3
   python -m http.server 8000

   # Using Node.js
   npx serve

   # Using PHP
   php -S localhost:8000
   ```

3. Open your browser to `http://localhost:8000`

### Editing

The website is entirely self-contained in `index.html`. All CSS is embedded in the `<style>` tag and all JavaScript is inline. This design choice makes the site:
- Easy to deploy
- Fast to load (single HTTP request)
- Simple to maintain

## Deployment

This site is configured for deployment on GitHub Pages:

1. Push changes to the `main` branch
2. GitHub Pages automatically serves the site from the repository root
3. The `CNAME` file configures the custom domain `lilicad.com`

### Manual Deployment

To deploy elsewhere, simply upload all files to your web server's root directory, ensuring:
- Directory structure is preserved
- Server supports custom domain configuration (if using CNAME)
- HTTPS is enabled for security

## Download Links

Download links in the website point to GitHub Releases. To update versions:

1. Create a new release in the main LiliCAD repository
2. Update the version number and URLs in `index.html` (lines 556-567)
3. Commit and push changes

Current version: **v0.1.1**

## Performance Optimizations

- Self-hosted fonts with `font-display: swap`
- Optimized images (consider WebP format for further optimization)
- Minimal external dependencies (only Bootstrap and Google Analytics)
- CSS custom properties for theming
- Reduced motion support for accessibility

## Browser Support

- Chrome/Edge: Latest 2 versions
- Firefox: Latest 2 versions
- Safari: Latest 2 versions
- Mobile browsers: iOS Safari, Chrome Android

## Analytics

The site uses Google Analytics (G-0V8WSD7C3S). To modify or remove:
- Edit or remove the gtag.js script block in the `<head>` section (lines 5-13)

## License

Copyright © LiliCAD. All rights reserved.

## Support

For help and support, contact: [support@lilicad.com](mailto:support@lilicad.com)

## Contributing

This is the official website repository. For bug reports or feature requests related to the LiliCAD application itself, please contact support.

---

Built with care for the 3D printing and CAD community.
