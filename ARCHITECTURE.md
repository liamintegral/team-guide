# 🏗️ Architecture Documentation

> **Complete technical architecture overview for Integral Media Project**

## 📋 Table of Contents
- [🎯 System Overview](#-system-overview)
- [🏛️ Architecture Patterns](#️-architecture-patterns)
- [🧩 Component Catalog](#-component-catalog)
- [📡 Data Flow](#-data-flow)
- [🔌 External Integrations](#-external-integrations)
- [📱 Responsive Strategy](#-responsive-strategy)

---

## 🎯 System Overview

### **Application Type**
- **Single Page Application (SPA)** - No routing, all content in one HTML file
- **Static Site** - No server-side processing, deployable to any web host
- **Progressive Enhancement** - Core functionality works without JavaScript

### **Technology Stack**
```
Frontend:
├── HTML5 (Semantic structure)
├── CSS3 (Custom properties, Grid, Flexbox)
└── Vanilla JavaScript (ES6+, EmailJS integration)

External Services:
├── EmailJS (Direct email submission)
├── Font Awesome 6.0.0 (Icon system)
└── Google Fonts (Typography fallbacks)

Deployment:
├── GitHub (Version control)
├── Vercel (Static hosting)
└── Custom domain support
```

### **File Architecture**
```
📁 Project Root/
├── 📄 index.html                    # Main application (~65KB with expanded content)
├── 📄 STYLE-GUIDE.md               # Design system documentation
├── 📄 ARCHITECTURE.md              # This file - technical documentation
├── 📄 CLAUDE.md                    # Development session documentation
├── 📄 README.md                    # Project overview and quick start
├── 📄 DEPLOYMENT.md                # Deployment instructions and configuration
├── 📄 .gitignore                   # Git exclusion patterns
│
├── 📁 css/
│   └── 📄 main.css                 # Consolidated stylesheet (15KB)
│
├── 📁 documentation/               # Specialised content
│   ├── 📄 industry-specific-considerations.html
│   └── 📄 kind-kitchens-remarketing-brief.html
│
├── 📁 archive/                     # Previous versions
│   ├── 📄 integral-media-complete-guide.html
│   └── 📁 styles/
│
└── 📁 archive-redundant-files/     # Archived redundant content
    ├── 📄 client-risk-assessment-system.html
    └── [4 other archived files]
```

---

## 🏛️ Architecture Patterns

### **1. Component-Based Design**
Even without a framework, the application follows component-based principles:

```css
/* Component Pattern Example */
.focus-area {
    /* Container styles */
}
.focus-area .focus-icon { /* Icon element */ }
.focus-area h3 { /* Title element */ }
.focus-area p { /* Description element */ }
.focus-area .focus-highlights { /* List element */ }
```

### **2. CSS Custom Properties Architecture**
```css
:root {
    /* Design tokens - single source of truth */
    --sidebar-width: 280px;
    --integral-blue: #214e9c;
    --integral-blue-light: #5cb3f0;
    /* Used throughout the entire system */
}
```

### **3. Mobile-First Responsive Design**
```css
/* Base styles for mobile */
.component {
    /* Mobile styles */
}

/* Desktop enhancements */
@media (min-width: 768px) {
    .component {
        /* Desktop styles */
    }
}
```

### **4. Progressive Enhancement**
1. **HTML Foundation** - Semantic structure works without CSS
2. **CSS Enhancement** - Visual design and layout
3. **JavaScript Enhancement** - Interactive features (feedback widget)

---

## 🧩 Component Catalog

### **Layout Components**

#### **1. Fixed Sidebar Navigation**
```css
.sidebar {
    position: fixed;
    width: var(--sidebar-width);
    height: 100vh;
    /* Always visible on desktop, slide-out on mobile */
}
```

**Features:**
- Hierarchical menu structure with collapsible sections
- Smooth scrolling navigation to page anchors
- Active state indicators
- Mobile responsive with overlay

**Data Attributes:**
- `data-target` - Scroll target for navigation items
- `data-section` - Section identifier for active states

#### **2. Main Content Area**
```css
.main-content {
    margin-left: var(--sidebar-width);
    /* Offset by sidebar width on desktop */
}
```

**Features:**
- Automatic offset for sidebar width
- Full-width on mobile devices
- Maximum content width constraint (1200px)

#### **3. Top Header**
```css
.top-header {
    height: 101.27px; /* Exactly matched to sidebar header */
    padding: 1.5rem 2rem;
}
```

**Purpose:**
- Page title and subtitle display
- Mobile menu toggle button
- Consistent height alignment with sidebar header

### **Content Components**

#### **1. Focus Areas (Three-Column Layout)**
```css
.overview-focus-areas {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}
```

**Use Cases:**
- **Core Sections**: Overview, Time Tracking, Client Communication, Task Management, Performance Monitoring
- **Operational Sections**: Daily, Weekly, Monthly, Quarterly & Six-Monthly responsibilities
- **Service-Specific Sections**: SEO, PPC, Website service responsibilities
- **Standards Sections**: Communication Guidelines & Performance Standards

**Component Structure:**
```html
<div class="overview-focus-areas">
    <div class="focus-area">
        <div class="focus-icon"><i class="fas fa-icon"></i></div>
        <h3>Focus Area Title</h3>
        <p>Description paragraph</p>
        <ul class="focus-highlights">
            <li>Highlight item 1</li>
            <li>Highlight item 2</li>
        </ul>
    </div>
</div>
```

#### **2. Legacy Traditional Cards (Now Deprecated)**
```css
/* Legacy card pattern - replaced by focus-area design */
.card {
    background: var(--neutral-white);
    margin-bottom: 2rem;
}
```

**Previous Use Cases (Now Converted):**
- All sections now use the three-column focus-area layout
- Legacy card pattern maintained for reference only
- Complete design consistency achieved across all 14 sections

**Component Structure:**
```html
<div class="card">
    <h4>Card Header</h4>
    <div class="card-content">
        <p>Card content</p>
        <ul><li>List items</li></ul>
    </div>
</div>
```

#### **3. Highlight Boxes**
```css
.highlight-box {
    background: var(--integral-blue-light);
    color: var(--neutral-white);
    padding: 1rem 1.5rem;
}
```

**Purpose:**
- Important callouts and emphasis
- Key takeaways and summaries
- Action-oriented messaging

### **Interactive Components**

#### **1. Floating Feedback Widget**
```javascript
// Widget State Management
const FeedbackWidget = {
    isOpen: false,
    currentSection: 0,
    userInfo: {},
    sectionFeedback: {},
    // Methods for state management
};
```

**Component Architecture:**
- **Toggle Button** - Floating circular button (top-right)
- **Panel Overlay** - Modal-style feedback collection form
- **Progress Tracking** - Visual indicators for completion
- **Section Navigation** - Jump between feedback sections

**State Management:**
- User information persistence (localStorage)
- Section feedback tracking (in-memory object)
- Progress calculation and visual updates
- EmailJS integration for submission

---

## 📡 Data Flow

### **1. Static Content Flow**
```
HTML Structure → CSS Styling → Visual Rendering
     ↑               ↑              ↑
Semantic markup → Design tokens → User interface
```

### **2. Navigation Flow**
```
User Click → Smooth Scroll → Update Active States → Visual Feedback
    ↓             ↓               ↓                    ↓
Navigation → Page Section → Sidebar Highlight → User Orientation
```

### **3. Feedback Widget Flow**
```
Widget Toggle → User Info Form → Section Navigation → Feedback Collection
      ↓              ↓                ↓                     ↓
Panel Open → Form Validation → Progress Updates → Data Aggregation
      ↓              ↓                ↓                     ↓
User Session → Local Storage → Visual Progress → Email Submission
```

### **4. Responsive Adaptation Flow**
```
Viewport Resize → Media Query Trigger → Layout Recalculation → Component Adaptation
       ↓                 ↓                     ↓                      ↓
Screen Size → CSS Rules Applied → Grid Reorganization → Mobile UX
```

---

## 🔌 External Integrations

### **1. EmailJS Integration**

#### **Configuration**
```javascript
emailjs.init({
    publicKey: "Yb9XsQ_h3DSDJ_bIA",
});

// Service and template configuration
const SERVICE_ID = 'service_p2fplrx';
const TEMPLATE_ID = 'template_35rncws';
```

#### **Data Structure**
```javascript
// Template parameters sent to EmailJS
{
    user_name: "User's Name",
    user_email: "user@example.com", 
    feedback_summary: "Aggregated feedback from all sections",
    sections_completed: "25/33",
    submission_date: "2025-07-22 14:30:00"
}
```

#### **Error Handling**
- Network failure fallback messages
- Validation for required fields
- User feedback for successful submissions
- Retry mechanisms for failed sends

### **2. Font Awesome Integration**
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
```

**Icon Usage Pattern:**
- Navigation: `fa-home`, `fa-clock`, `fa-users`, etc.
- Focus Areas: `fa-comments`, `fa-tasks`, `fa-chart-line`
- UI Elements: `fa-chevron-right`, `fa-check`, `fa-times`

**Performance Consideration:**
- CDN delivery for fast loading
- Subset loading could be implemented for optimization
- Fallback text for accessibility when icons fail to load

---

## 📱 Responsive Strategy

### **Breakpoint Strategy**
```css
/* Mobile First - Base styles */
/* Everything below 768px gets mobile treatment */

@media (max-width: 768px) {
    /* Mobile-specific overrides */
    .sidebar { transform: translateX(-100%); }
    .overview-focus-areas { grid-template-columns: 1fr; }
    .main-content { margin-left: 0; }
}
```

### **Layout Adaptations**

#### **Desktop (>768px)**
- **Sidebar**: Fixed 280px width, always visible
- **Content**: Offset by sidebar width, max-width 1200px
- **Grid**: 3-column layouts for focus areas
- **Navigation**: Hierarchical with hover states

#### **Mobile (≤768px)**
- **Sidebar**: Hidden by default, slide-out with overlay
- **Content**: Full width, no offset
- **Grid**: Single column, stacked vertically
- **Navigation**: Touch-friendly with larger tap targets

### **Performance Considerations**

#### **Critical Rendering Path**
1. **HTML parsed** - Semantic structure loaded first
2. **CSS loaded** - External stylesheet (main.css)
3. **Font Awesome** - Icon font from CDN
4. **JavaScript** - EmailJS and widget functionality

#### **Loading Strategy**
- **Above-the-fold content** prioritized in HTML
- **CSS optimized** for rendering speed
- **JavaScript** loaded asynchronously for enhanced features
- **Images optimized** (minimal use, SVGs preferred)

---

## 🔧 Technical Implementation Details

### **CSS Architecture Patterns**

#### **BEM-Inspired Naming**
```css
/* Block - Component */
.focus-area { }

/* Element - Part of component */
.focus-area__icon { }
.focus-area__title { }
.focus-area__highlights { }

/* Modifier - Variant */
.focus-area--highlighted { }
```

#### **Utility Classes**
```css
/* Minimal utility classes for common needs */
.mb-2 { margin-bottom: 0.5rem; }
.text-center { text-align: center; }
.font-bold { font-weight: 700; }
```

### **JavaScript Patterns**

#### **Module Pattern**
```javascript
// Encapsulated functionality
const FeedbackWidget = (function() {
    // Private variables and methods
    let isOpen = false;
    
    // Public interface
    return {
        toggle: function() { /* implementation */ },
        init: function() { /* implementation */ }
    };
})();
```

#### **Event Delegation**
```javascript
// Single event listener for multiple elements
document.addEventListener('click', function(e) {
    if (e.target.matches('.nav-item')) {
        // Handle navigation
    }
    if (e.target.matches('.feedback-toggle')) {
        // Handle feedback widget
    }
});
```

---

**Last Updated**: 2025-07-22  
**Version**: 1.0 (Production Architecture)  
**Compatible with**: Modern browsers, static hosting platforms

*Technical foundation for scalable development*