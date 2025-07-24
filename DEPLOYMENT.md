# 🚀 Deployment & Maintenance Guide

> **Complete deployment workflows and maintenance procedures for Integral Media Client Facing Team Project**

## 📋 Table of Contents
- [🎯 Quick Deployment](#-quick-deployment)
- [🔧 Platform Setup](#-platform-setup)
- [⚙️ Configuration](#️-configuration)
- [📊 Monitoring](#-monitoring)
- [🔄 Maintenance](#-maintenance)
- [🚨 Troubleshooting](#-troubleshooting)

---

## 🎯 Quick Deployment

### **1-Click Vercel Deployment**
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/liamintegral/team-guide)

### **Manual Deployment Steps**
```bash
# 1. Clone repository
git clone https://github.com/liamintegral/team-guide.git
cd team-guide

# 2. Verify files
ls -la
# Should see: index.html, css/, documentation/, etc.

# 3. Test locally
open index.html
# Verify all sections load and feedback widget works

# 4. Deploy to Vercel
npm install -g vercel  # If not already installed
vercel --prod
```

### **Alternative Platforms**

#### **Netlify Drag & Drop**
1. Visit [Netlify Drop](https://app.netlify.com/drop)
2. Drag entire project folder to deployment area
3. Site deploys automatically with generated URL
4. Configure custom domain in site settings

#### **GitHub Pages**
```bash
# Enable GitHub Pages in repository settings
# Set source to main branch / root folder
# Site available at: https://username.github.io/repository-name
```

---

## 🔧 Platform Setup

### **Vercel Configuration**

#### **Project Settings**
```json
{
  "name": "integral-media-team-guide",
  "version": 2,
  "builds": [
    {
      "src": "index.html",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/$1"
    }
  ]
}
```

#### **Environment Variables** (if needed)
```bash
# In Vercel dashboard: Settings → Environment Variables
EMAILJS_PUBLIC_KEY=Yb9XsQ_h3DSDJ_bIA
EMAILJS_SERVICE_ID=service_p2fplrx
EMAILJS_TEMPLATE_ID=template_35rncws
```

#### **Custom Domain Setup**
1. **Vercel Dashboard** → Project → Settings → Domains
2. **Add Domain** → Enter custom domain
3. **Configure DNS** at domain registrar:
   ```
   Type: A
   Name: @
   Value: 76.76.19.61 (Vercel IP)
   
   Type: CNAME  
   Name: www
   Value: cname.vercel-dns.com
   ```
4. **SSL Certificate** - Automatically provisioned

### **Netlify Configuration**

#### **netlify.toml**
```toml
[build]
  publish = "."
  
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "DENY"
    X-XSS-Protection = "1; mode=block"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"

# Redirect rules for SPA behaviour
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

### **Firebase Hosting**

#### **firebase.json**
```json
{
  "hosting": {
    "public": ".",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ],
    "headers": [
      {
        "source": "**/*.@(css|js)",
        "headers": [
          {
            "key": "Cache-Control",
            "value": "max-age=31536000"
          }
        ]
      }
    ]
  }
}
```

---

## ⚙️ Configuration

### **EmailJS Setup Verification**

#### **Testing Email Integration**
```javascript
// Test EmailJS configuration in browser console
emailjs.send('service_p2fplrx', 'template_35rncws', {
    user_name: 'Test User',
    user_email: 'test@example.com',
    feedback_summary: 'Test feedback submission',
    sections_completed: '1/24',
    submission_date: new Date().toLocaleString()
}).then(function(response) {
    console.log('SUCCESS!', response.status, response.text);
}, function(error) {
    console.log('FAILED...', error);
});
```

#### **Email Template Requirements**
**Template ID**: `template_35rncws`
**Required Variables:**
- `{{user_name}}` - Feedback submitter name
- `{{user_email}}` - Submitter email for follow-up  
- `{{feedback_summary}}` - Aggregated feedback from all sections
- `{{sections_completed}}` - Progress indicator (e.g., "12/24")
- `{{submission_date}}` - Timestamp of submission

### **Performance Optimisation**

#### **Asset Optimisation Checklist**
- [ ] **HTML minification** - Remove unnecessary whitespace
- [ ] **CSS consolidation** - Single external stylesheet
- [ ] **Image optimisation** - Use SVGs for icons, optimize any images
- [ ] **Font loading** - Optimise web font loading strategy
- [ ] **JavaScript bundling** - Consider bundling if adding more scripts

#### **Caching Strategy**
```html
<!-- Add to <head> for optimal caching -->
<meta http-equiv="Cache-Control" content="max-age=31536000">
<link rel="preload" href="css/main.css" as="style">
<link rel="dns-prefetch" href="//cdnjs.cloudflare.com">
```

---

## 📊 Monitoring

### **Performance Monitoring**

#### **Core Web Vitals Tracking**
- **LCP (Largest Contentful Paint)** - Should be < 2.5s
- **FID (First Input Delay)** - Should be < 100ms  
- **CLS (Cumulative Layout Shift)** - Should be < 0.1

#### **Monitoring Tools**
1. **Google PageSpeed Insights**
   - URL: https://pagespeed.web.dev/
   - Check both mobile and desktop performance
   - Target: 90+ score on both platforms

2. **Vercel Analytics** (if using Vercel)
   - Automatic performance monitoring
   - Real user metrics (RUM)
   - Error tracking and alerts

3. **Google Analytics** (optional)
   ```html
   <!-- Add to <head> if analytics needed -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=GA_TRACKING_ID"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'GA_TRACKING_ID');
   </script>
   ```

### **EmailJS Monitoring**

#### **Email Delivery Tracking**
- **EmailJS Dashboard** - Monitor send quotas and success rates
- **Email deliverability** - Check spam folder if emails not received
- **Template validation** - Ensure all variables are properly mapped

#### **Quota Management**
- **Free Tier**: 200 emails/month
- **Pro Tier**: 50,000 emails/month
- **Monitor usage** in EmailJS dashboard
- **Set up alerts** for quota limits

---

## 🔄 Maintenance

### **Regular Maintenance Tasks**

#### **Weekly Tasks**
- [ ] **Test feedback widget** - Submit test feedback to ensure email delivery
- [ ] **Check broken links** - Verify all internal navigation works
- [ ] **Mobile testing** - Test responsive design on various devices
- [ ] **Performance check** - Run PageSpeed Insights audit

#### **Monthly Tasks**
- [ ] **Update dependencies** - Font Awesome, any CDN resources
- [ ] **Review EmailJS usage** - Check quota consumption
- [ ] **Backup content** - Ensure latest version in git repository
- [ ] **Security audit** - Check for any security updates needed

#### **Quarterly Tasks**
- [ ] **Content review** - Update team information and procedures
- [ ] **Design refresh** - Consider UI improvements based on feedback
- [ ] **Performance optimisation** - Analyse and optimise loading times
- [ ] **Accessibility audit** - Ensure WCAG compliance

### **Content Updates**

#### **Team Information Updates**
**File**: `index.html`
**Sections to Update**:
- Account Manager names and portfolios
- Contact information
- Reporting structure
- Portfolio values

#### **Procedure Updates**
**Common Changes**:
- New software tools or platforms
- Updated communication protocols  
- Modified reporting requirements
- New compliance procedures

#### **Design System Updates**
**Files to Modify**:
- `css/main.css` - Visual design changes
- `STYLE-GUIDE.md` - Document design system changes
- `index.html` - Structural modifications

### **Version Control Workflow**

#### **Standard Git Workflow**
```bash
# 1. Pull latest changes
git pull origin main

# 2. Make changes to files
# Edit index.html, css/main.css, etc.

# 3. Test changes locally
open index.html
# Verify all functionality works

# 4. Commit changes
git add .
git commit -m "Update team information and procedures

- Updated account manager portfolios
- Added new software tool documentation
- Fixed mobile navigation issue

🤖 Generated with Claude Code

Co-Authored-By: Claude <noreply@anthropic.com>"

# 5. Push to repository
git push origin main

# 6. Verify deployment
# Check live site in 1-2 minutes
```

---

## 🚨 Troubleshooting

### **Common Issues**

#### **1. Feedback Widget Not Working**

**Symptoms:**
- Widget button doesn't open panel
- Email submissions fail
- JavaScript console errors

**Solutions:**
```javascript
// Check EmailJS configuration
console.log('EmailJS loaded:', typeof emailjs !== 'undefined');

// Test widget initialization
if (typeof FeedbackWidget !== 'undefined') {
    console.log('Widget loaded successfully');
} else {
    console.error('Widget failed to load');
}

// Verify EmailJS credentials
emailjs.init({
    publicKey: "Yb9XsQ_h3DSDJ_bIA", // Verify this key is correct
});
```

#### **2. Mobile Layout Issues**

**Symptoms:**
- Sidebar doesn't slide out on mobile
- Three-column layouts don't stack
- Touch targets too small

**Solutions:**
```css
/* Debug mobile styles */
@media (max-width: 768px) {
    .sidebar {
        transform: translateX(-100%); /* Ensure sidebar hides */
    }
    
    .overview-focus-areas {
        grid-template-columns: 1fr !important; /* Force single column */
    }
}
```

#### **3. Performance Issues**

**Symptoms:**
- Slow loading times
- Large file sizes
- Poor PageSpeed scores

**Solutions:**
1. **Optimise CSS**
   ```bash
   # Remove unused CSS rules
   # Combine multiple stylesheets
   # Minify CSS for production
   ```

2. **Optimise Images**
   ```bash
   # Convert images to WebP format
   # Use SVGs for icons
   # Implement lazy loading if needed
   ```

3. **Optimise Fonts**
   ```html
   <!-- Preload critical fonts -->
   <link rel="preload" href="path/to/font.woff2" as="font" type="font/woff2" crossorigin>
   ```

### **Emergency Procedures**

#### **Site Down/Broken**
1. **Check deployment status** in hosting platform dashboard
2. **Revert to last working commit**:
   ```bash
   git log --oneline
   git revert [problematic-commit-hash]
   git push origin main
   ```
3. **Emergency fallback**: Deploy from archive folder if needed

#### **EmailJS Service Issues**
1. **Check EmailJS status** at status.emailjs.com
2. **Verify credentials** in EmailJS dashboard
3. **Temporary fallback**: Add mailto links as backup
   ```html
   <!-- Emergency fallback -->
   <a href="mailto:liam@integralmedia.com.au?subject=Feedback">Send Feedback</a>
   ```

#### **DNS/Domain Issues**
1. **Check DNS propagation** at whatsmydns.net
2. **Verify domain settings** in hosting platform
3. **Contact domain registrar** if DNS issues persist

---

## 📈 Scaling Considerations

### **Traffic Growth**
- **Static hosting** scales automatically for most platforms
- **CDN optimisation** for global performance
- **Monitoring alerts** for unusual traffic patterns

### **Feature Additions**
- **Maintain single-file architecture** for simplicity
- **Consider build process** if complexity increases
- **Update documentation** when adding features

### **Team Growth**
- **Update team information** sections
- **Scale feedback system** for more users
- **Consider user authentication** if needed for personalization

---

**Last Updated**: 2025-07-22  
**Version**: 1.0 (Production Deployment Guide)  
**Compatible with**: Vercel, Netlify, GitHub Pages, Firebase

*Complete deployment and maintenance workflows for reliable operations*