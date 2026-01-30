# Urulooke - Agent Coding Guide

This is a static HTML website about health and wellness with Spanish content. No build system, package managers, or testing frameworks are in use.

## Development Workflow

### Running the Site
Open `index.html` directly in a browser or serve with any static file server:
```bash
python -m http.server 8000
# or
npx serve
```

### File Structure
- `index.html` - Homepage with card-based navigation grid
- `*.html` - Individual content pages with sidebar navigation
- `images/` - All image assets (JPG, ICO, JPEG formats)

## Code Style Guidelines

### HTML Structure
- Use `<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">` for content pages
- Use `<html>` (no DOCTYPE) for index.html (existing pattern)
- Include `<meta charset="UTF-8">` and viewport meta tag
- Link external font: `<link rel="stylesheet" href="https://use.typekit.net/oov2wcw.css">`
- Set favicon: `<link rel="icon" href="images/dragon_blue_background_32.ico" type="image/x-icon">`

### CSS Conventions
- All styles in `<style>` tags within `<head>` section (no external CSS files)
- Use century-gothic font family: `font-family: century-gothic, sans-serif;`
- Primary colors: `#4682b4` (steel blue), `#3498db` (blue), `#2c3e50` (dark blue-gray)
- Responsive breakpoints: 768px (mobile), 1024px (tablet)
- Use flexbox for layouts: `display: flex;` with `flex: 1` for content areas
- Sidebar fixed width: `250px`
- Container opacity: `0.80` or `0.85` for readability over backgrounds
- Include both `-webkit-` and standard prefix for animations

### JavaScript Conventions
- Wrap in `DOMContentLoaded` event listener:
  ```javascript
  document.addEventListener('DOMContentLoaded', function() { ... });
  ```
- Use `const` for element queries: `const element = document.querySelector('.selector');`
- Mobile menu toggle pattern: toggle `.active` class on sidebar
- Handle window resize to remove `.active` class when screen expands

### Responsive Design
- Mobile first approach with `@media (max-width: 768px)` queries
- Transform sidebar with `translateX(-100%)` on mobile
- Menu toggle button displays only on mobile
- Use `.sidebar.active` to show/hide mobile menu
- Close menu when clicking outside on mobile screens

### Navigation Pattern
- All content pages include sidebar with navigation links
- Sidebar structure:
  ```html
  <div class="sidebar">
      <h2><a href="index.html">Home</a></h2>
      <ul class="menu">
          <li><a href="page.html">Page Title</a></li>
          ...
      </ul>
  </div>
  ```
- Card navigation on index.html uses `data-page` attribute:
  ```html
  <div class="card" data-page="page-name">
      <img src="images/image.jpg" alt="Description" width="400" height="200">
      <h3>Title</h3>
  </div>
  ```

### Naming Conventions
- HTML files: lowercase with hyphens (e.g., `salud-financiera.html`)
- Image files: lowercase with hyphens (e.g., `financial-health.jpg`)
- CSS classes: lowercase with hyphens (e.g., `.menu-toggle`, `.sidebar-active`)
- Use descriptive, semantic class names

### Content Guidelines
- All content is in Spanish
- Use HTML entities for special characters: `&aacute;`, `&eacute;`, `&oacute;`, `&ntilde;`
- Image `alt` attributes should be descriptive Spanish text
- Hierarchy: `<h1>` for page title, `<h2>` for sections, `<h3>` for subsections

### Adding New Pages
1. Create new HTML file following naming pattern
2. Copy sidebar structure from existing pages
3. Add corresponding card to `index.html`
4. Add navigation link to all existing pages' sidebar menus
5. Include relevant image in `images/` directory
6. Follow existing styling patterns (adjust colors as needed)

### Glow Animation
- Apply `.glow` class to main headings
- Animation defined with keyframes from white to blue glow
- Used for emphasis on page titles

### Card Component (index.html)
- Cards use `data-page` attribute for navigation routing
- Image dimensions: `width="400" height="200"` in HTML attributes
- CSS enforces height with `object-fit: cover` for consistent aspect ratio
- Hover effects include translateY(-5px) and enhanced box-shadow
- Grid layout: 3 columns on desktop, 2 on tablet (1024px), 1 on mobile (768px)

### Article Container
- Content pages use `.article` class for main content wrapper
- White background with border-radius: 8px
- Padding: 20px, box-shadow: 0 2px 4px rgba(0,0,0,0.1)
- Contains H2 sections and paragraph content
- Lists use standard `<ul>` and `<li>` elements

### Background Images
- Each page has a unique background image from `images/` directory
- Background properties:
  ```css
  background-image: url("images/page-name.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  ```
- Fallback background color: `#cccccc` or similar
- Some pages also set `background-color: #f0f8ff` (AliceBlue)

### Typography Scale
- H1 (page titles): 2.5em on content pages, 3em on index
- H2 (sections): 1.8em on content pages, 1.5em on index
- H3 (subsections): Default size
- Paragraphs: Default size, color: #333
- Link text: White (#ecf0f1) with blue (#3498db) hover state

### Mobile Menu Behavior
- Toggle button (`☰` character) shows on screens <= 1024px
- Sidebar uses fixed positioning with `transform: translateX(-100%)` when hidden
- `.active` class transforms to `translateX(0)` to show menu
- Menu closes when clicking outside the sidebar on mobile
- Menu automatically closes when window resizes above 768px
- Content shifts to `padding-top: 60px` when menu is open on mobile

### Browser Compatibility
- Include vendor prefixes for animations: `-webkit-`, `-moz-`
- Use standard CSS properties alongside vendor prefixes
- Test in modern browsers (Chrome, Firefox, Safari, Edge)
- Glow animation needs -webkit- prefix for Safari compatibility

### Accessibility
- All images include descriptive `alt` attributes in Spanish
- Navigation links are clearly labeled with page titles
- Color contrast meets WCAG guidelines (white on blue, dark on light)
- Semantic HTML structure with proper heading hierarchy
- Focus states not explicitly styled but use browser defaults
