# 🎨 Integral Media Client Facing Team Project - Style Guide

> **Comprehensive design system and development guidelines for Claude Code sessions**

## 📋 Table of Contents
- [🎯 Design Principles](#-design-principles)  
- [🎨 Colour System](#-color-system)
- [📝 Typography](#-typography)
- [🧩 Component Patterns](#-component-patterns)
- [📱 Responsive Design](#-responsive-design)
- [⚙️ Development Guidelines](#️-development-guidelines)
- [🔧 Technical Standards](#-technical-standards)

---

## 🎯 Design Principles

### **Core Values**
1. **Modern Flat Design** - Clean, professional appearance without unnecessary shadows or depth effects
2. **Professional Excellence** - Corporate design suitable for business environment with comprehensive context
3. **Accessibility First** - Clear hierarchy, readable text, proper contrast ratios
4. **Mobile Responsive** - Seamless experience across all devices
5. **Consistent Experience** - Standardized patterns and predictable interactions
6. **Performance Focussed** - Optimized for fast loading and smooth interactions

### **Visual Philosophy**
- **Flat Design Principles** - Modern appearance with subtle borders instead of shadows
- **Contextual Clarity** - Section summaries provide purpose and understanding before content
- **Minimalist Design** - Clean layouts with purposeful whitespace
- **Professional Aesthetics** - Corporate-friendly colour scheme and typography
- **Functional Beauty** - Every design element serves a purpose
- **Scalable System** - Components that work at any size or context

---

## 🎨 Colour System

### **Primary Brand Colours**
```css
/* Integral Media Brand Colours */
--integral-blue: #214e9c;        /* Primary brand colour */
--integral-blue-light: #5cb3f0;  /* Accents and highlights */
--integral-blue-dark: #1e3a8a;   /* Headers and emphasis */
```

### **Neutral Palette**
```css
/* Neutral Colors for UI Elements */
--neutral-white: #ffffff;        /* Pure white backgrounds */
--neutral-gray-50: #f9fafb;     /* Light background */
--neutral-gray-100: #f3f4f6;    /* Card backgrounds */
--neutral-gray-200: #e5e7eb;    /* Borders and dividers */
--neutral-gray-300: #d1d5db;    /* Form borders */
--neutral-gray-600: #4b5563;    /* Secondary text */
--neutral-gray-700: #374151;    /* Primary text */
--neutral-gray-800: #1f2937;    /* Dark text and headers */
```

### **Functional Colors**
```css
/* Feedback System Colors */
--success-green: #28a745;       /* Good feedback buttons */
--warning-yellow: #ffc107;      /* Needs work buttons */  
--info-blue: #17a2b8;          /* Suggestion buttons */
--danger-red: #e74c3c;         /* Error states and badges */
```

### **Usage Guidelines**
- **Primary Blue** (`#214e9c`) - Main navigation, headers, primary actions
- **Light Blue** (`#5cb3f0`) - Icons, accents, highlight boxes
- **Dark Blue** (`#1e3a8a`) - Section headers, emphasis text
- **Neutral Grays** - Body text, backgrounds, borders (maintain contrast ratios)

---

## 📝 Typography

### **Font Stack**
```css
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
```

### **Type Scale**
```css
/* Heading Hierarchy */
h1: 1.5rem   (24px) - Page titles
h2: 1.25rem  (20px) - Major section headers
h3: 1.125rem (18px) - Focus area titles
h4: 1rem     (16px) - Card headers
h5: 0.9rem   (14px) - Minor headings

/* Body Text */
body: 0.9rem (14px) - Main content
small: 0.85rem (13px) - Secondary text
caption: 0.8rem (12px) - Form labels, navigation
```

### **Font Weights**
- **400** (Normal) - Body text, standard content
- **500** (Medium) - Card headers, form labels
- **600** (Semibold) - Focus area titles, important headings

### **Line Heights**
- **Body Text**: 1.6 (optimal readability)
- **Headers**: 1.2-1.3 (tighter for impact)
- **Small Text**: 1.4-1.5 (legible at smaller sizes)

---

## 🧩 Component Patterns

### **1. Section Summary Pattern**
> **Contextual introduction for all major sections**

```css
.section-summary {
    background: var(--neutral-gray-50);
    padding: 1.5rem 2rem;
    margin: 0 0 2rem 0;
    border-radius: 4px;
    border-left: 4px solid var(--integral-blue-light);
}
```

**Structure:**
- **Light Background** - Subtle gray-50 background for distinction
- **Blue Accent Border** - Left border in brand light blue
- **Italic Text** - Professional context setting with proper typography
- **Strategic Purpose** - Explains section importance and objectives

**When to Use:**
- **All Major Sections**: Provides context before diving into focus areas
- **User Understanding**: Helps users understand section purpose and relevance
- **Professional Presentation**: Elevates content with strategic context

### **2. Three-Column Focus Areas**
> **Primary layout pattern for major sections**

```css
.overview-focus-areas {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin: 2rem 0;
}
```

**Structure:**
- **Icon Circle** - 60px diameter, brand colour background
- **Heading** - h3 element, dark blue colour
- **Description** - Gray body text with good line height
- **Highlight List** - Checkmark bullets, organised items
- **Flat Design** - Subtle borders with hover effects (no shadows)

**When to Use:**
- **Universal Application**: Now used across ALL content sections for design consistency
- **Core Sections**: Overview, Time Tracking, Client Communication, Task Management, Performance Monitoring
- **Operational Sections**: Daily, Weekly, Monthly, Quarterly & Six-Monthly responsibilities  
- **Service-Specific Sections**: SEO, PPC, Website service responsibilities
- **Standards Sections**: Communication Guidelines & Performance Standards

### **3. Legacy Traditional Cards (Deprecated)**
> **Previous pattern - now replaced by focus-area design**

```css
/* Legacy pattern maintained for reference only */
.card {
    background: var(--neutral-white);
    padding: 0;
    margin-bottom: 2rem;
}

.card h4 {
    background: var(--integral-blue);
    color: var(--neutral-white);
    padding: 1rem 1.5rem;
}

.card .card-content {
    padding: 1.5rem;
}
```

**Status:**
- **DEPRECATED**: All sections converted to three-column focus-area layout
- **Design Consistency**: Achieved uniform visual treatment across all 14 sections
- **Legacy Reference**: Pattern preserved for historical context only

### **4. Targeted Feedback System**
> **Interactive feedback collection system**

**Key Features:**
- **Section-specific buttons** - Small circular buttons next to each section title
- **Targeted feedback** - Users click buttons for sections they want to provide feedback on
- **Visual state indicators** - Buttons turn green when feedback is provided
- **Collected feedback review** - Users can edit/remove individual feedback before submission
- **One-time setup** - Enter name/email once to enable all section buttons

**States:**
- **Hidden** - Section buttons hidden until user enters credentials
- **Available** - Blue circular buttons appear next to section titles
- **Has Feedback** - Green buttons indicate feedback provided
- **Panel States** - Floating widget shows collected feedback and submission options

### **5. Navigation Patterns**

#### **Sidebar Navigation**
- **Fixed width** - 280px on desktop
- **Hierarchical structure** - Main items with collapsible subitems
- **Smooth scrolling** - Anchored navigation to page sections
- **Mobile responsive** - Slides out on mobile with overlay

#### **Breadcrumb Alternative**
- Use **single page title** in top header instead of breadcrumbs
- Rely on **sidebar navigation** for site orientation
- Keep **header content minimal** and focused

---

## 📱 Responsive Design

### **Breakpoints**
```css
/* Mobile First Approach */
@media (max-width: 768px) {
    /* Mobile styles - single column layouts */
}

/* Desktop is default (above 768px) */
/* Three-column layouts, fixed sidebar */
```

### **Mobile Transformations**

#### **Grid Layouts**
- **Desktop**: 3 columns side-by-side
- **Mobile**: 1 column stacked vertically
- **Gap reduction** - 2rem → 1.5rem on mobile

#### **Navigation**
- **Desktop**: Fixed sidebar always visible
- **Mobile**: Hidden sidebar with hamburger menu
- **Overlay**: Dark background when mobile menu is open

#### **Feedback Widget**
- **Desktop**: 70px button, 400px panel
- **Mobile**: 60px button, full-width panel (minus 30px margins)

### **Content Priorities**
1. **Essential content first** - Core information visible immediately
2. **Progressive disclosure** - Secondary details in expandable sections
3. **Touch-friendly targets** - Minimum 44px tap targets on mobile
4. **Readable text** - Never smaller than 14px on mobile

---

## ⚙️ Development Guidelines

### **File Organization**
```
📁 Integral Media Project/
├── 📄 index.html                    # Single-page application
├── 📁 css/
│   └── 📄 main.css                  # Consolidated stylesheet
├── 📁 documentation/                # Specialized content files  
├── 📁 archive/                      # Previous versions
└── 📁 archive-redundant-files/      # Archived content
```

### **CSS Architecture**

#### **CSS Custom Properties**
```css
:root {
    /* Use CSS variables for all colours and measurements */
    --sidebar-width: 280px;
    --integral-blue: #214e9c;
    /* Define once, use everywhere */
}
```

#### **Naming Conventions**
- **BEM-inspired** - `.component-element--modifier`
- **Semantic naming** - `.focus-area`, `.feedback-widget`
- **Avoid generic classes** - No `.blue-button`, use `.feedback-toggle`

#### **Sass/CSS Organization**
1. **CSS Variables** - All custom properties at top
2. **Reset Styles** - Universal box-sizing, margin/padding reset
3. **Base Styles** - Body, typography, fundamental elements
4. **Layout Components** - Sidebar, main content, grid systems
5. **UI Components** - Cards, widgets, forms
6. **Utility Classes** - Margin, text alignment, display helpers

### **JavaScript Patterns**

#### **EmailJS Integration**
```javascript
// Initialize once with public key
emailjs.init({
    publicKey: "Yb9XsQ_h3DSDJ_bIA",
});

// Template-based sending
emailjs.send(
    'service_p2fplrx',
    'template_35rncws',
    templateParams
);
```

#### **Widget State Management**
- **Simple object** - Track user info and section feedback
- **Local storage** - Persist user details across sessions
- **Progress tracking** - Visual indicators for completion

---

## 🔧 Technical Standards

### **Performance Requirements**
- **File size** - Main HTML file under 100KB
- **Load time** - Initial page load under 2 seconds
- **Image optimisation** - Use SVGs for icons, optimise any raster images
- **CSS efficiency** - Consolidated external stylesheet, no inline styles

### **Browser Support**
- **Modern browsers** - Chrome, Firefox, Safari, Edge (latest 2 versions)
- **ES6+ features** - Use modern JavaScript syntax
- **Progressive enhancement** - Core functionality works without JavaScript

### **Code Quality**
- **HTML semantic structure** - Proper heading hierarchy, meaningful elements
- **CSS maintainability** - Organized stylesheets, consistent naming
- **JavaScript reliability** - Error handling for EmailJS integration
- **Accessibility** - ARIA labels where needed, keyboard navigation support

### **Deployment Standards**
- **Git workflow** - Regular commits with descriptive messages
- **Static hosting** - Vercel or similar platform for deployment
- **Domain configuration** - Custom domain support in hosting platform
- **SSL certificate** - HTTPS enforced for security

---

## 🎯 Implementation Checklist

### **Before Starting Development**
- [ ] Review existing project structure and components
- [ ] Understand current EmailJS configuration
- [ ] Check mobile responsiveness requirements
- [ ] Identify which sections need focus area treatment

### **During Development**
- [ ] Use CSS custom properties for colours and measurements  
- [ ] Test three-column layouts on desktop and mobile
- [ ] Ensure proper heading hierarchy (h1 → h2 → h3 → h4)
- [ ] Implement smooth scrolling navigation
- [ ] Test feedback widget functionality

### **Before Deployment**
- [ ] Validate HTML structure and semantics
- [ ] Test responsive design at multiple breakpoints
- [ ] Verify EmailJS integration with test submissions
- [ ] Check performance metrics (file size, load time)
- [ ] Test cross-browser compatibility

---

## 💡 Future Enhancement Guidelines

### **Adding New Sections**
1. **Use focus-area layout exclusively** - Maintain design consistency across all sections
2. **Follow established patterns** - Use `overview-focus-areas` and `focus-area` class structure
3. **Include appropriate icons** - Font Awesome icons matching section purpose
4. **Update navigation** - Add to sidebar with proper hierarchical structure and subitems
5. **Update feedback system** - Add new sections to JavaScript feedback tracking array
6. **Test responsiveness** - Ensure mobile optimisation and single-column stacking

### **Extending Feedback System**
- **Section tracking** - Update feedback sections array
- **Email templates** - Modify EmailJS template for new fields
- **Progress calculation** - Adjust completion percentages

### **Performance Optimisation**
- **Image optimisation** - Use WebP format where supported
- **CSS minification** - Consider build process for production
- **JavaScript bundling** - If adding more interactive features

---

## 📝 Language & Style Requirements

**⚠️ IMPORTANT: British English Only**
- This project uses **British English spelling exclusively**
- All content, documentation, and user-facing text must use British spellings
- Examples: optimise (not optimize), colour (not color), analyse (not analyze), organised (not organized)
- CSS property names remain unchanged as per web standards (e.g., `color`, `background-color`)

---

**Last Updated**: 2025-07-22  
**Version**: 2.0 (Complete Layout System)  
**Compatible with**: Claude Code development sessions

*Built with ❤️ for consistent, professional development*