# 🌟 Multi-Branch Development Guide

> **Complete guide for managing three parallel versions of the Integral Media Team Guide project**

## 📋 Branch Overview

### **🎯 Three Project Versions**

| Branch | Version | Description | Target Audience |
|--------|---------|-------------|-----------------|
| **`main`** | **Client Facing Team Guide** | Comprehensive operational guide with full features | Account Managers, Client-facing staff |
| **`simplified-guide`** | **Essential Operations Guide** | Streamlined version focused on core daily tasks | Quick reference, new team members |
| **`interactive-guide`** | **Interactive Team Guide** | Enhanced version with advanced interactive features | Power users, collaborative workflows |

---

## 🏗️ Branch Structure

### **Shared Foundation**
All branches inherit from the same solid architecture:
- ✅ **CSS Framework**: Consistent design system with custom properties
- ✅ **Component Library**: Reusable focus-area layouts and navigation patterns  
- ✅ **Responsive Design**: Mobile-first approach with 768px breakpoint
- ✅ **EmailJS Integration**: Feedback system with service configuration
- ✅ **Documentation**: Comprehensive technical and style documentation

### **Branch-Specific Adaptations**

#### **🎯 Main Branch (`main`)**
- **Title**: "Client Facing Team Guide"
- **Content**: Full comprehensive guide with all 14 sections
- **Features**: Complete feedback system, all focus areas, comprehensive summaries
- **Deployment**: Primary production version

#### **📋 Simplified Guide (`simplified-guide`)**
- **Title**: "Essential Operations Guide"  
- **Content**: Streamlined content focusing on core daily operations
- **Features**: Simplified navigation, essential procedures only
- **Target**: Quick reference and onboarding

#### **⚡ Interactive Guide (`interactive-guide`)**
- **Title**: "Interactive Team Guide"
- **Content**: Enhanced with advanced interactive features
- **Features**: Real-time updates, collaboration tools, advanced productivity features
- **Target**: Power users and collaborative workflows

---

## 🔄 Development Workflow

### **Standard Git Operations**

#### **Switching Between Branches**
```bash
# View all branches
git branch -a

# Switch to specific version
git checkout main                    # Comprehensive version
git checkout simplified-guide        # Streamlined version  
git checkout interactive-guide       # Enhanced version
```

#### **Making Branch-Specific Changes**
```bash
# 1. Switch to target branch
git checkout simplified-guide

# 2. Make changes specific to that version
# Edit files, update content, modify features

# 3. Commit changes
git add .
git commit -m "Update simplified guide: [description]

🤖 Generated with Claude Code

Co-Authored-By: Claude <noreply@anthropic.com>"

# 4. Push to remote
git push origin simplified-guide
```

### **Merging Shared Improvements**

When you make improvements that benefit all versions (bug fixes, design improvements, etc.):

```bash
# 1. Make changes on main branch
git checkout main
# Fix bugs, improve design, update shared components
git add .
git commit -m "Fix shared component issue"

# 2. Merge improvements to other branches
git checkout simplified-guide
git merge main

git checkout interactive-guide  
git merge main

# 3. Push all branches
git push origin simplified-guide
git push origin interactive-guide
git push origin main
```

### **Resolving Merge Conflicts**

If branches have diverged significantly:

```bash
# If merge conflict occurs
git status                    # See conflicted files
# Edit files to resolve conflicts
git add .                     # Stage resolved files
git commit                    # Complete merge
```

---

## 🚀 Deployment Strategy

### **Recommended Hosting Setup**

#### **Vercel Multi-Branch Deployment**
1. **Connect GitHub Repository** to Vercel
2. **Enable Branch Deployments** in Vercel settings
3. **Custom Domains** for each version:

| Branch | Suggested Domain | Purpose |
|--------|------------------|---------|
| `main` | `team-guide.integralmedia.com.au` | Primary comprehensive guide |
| `simplified-guide` | `essential.integralmedia.com.au` | Quick reference version |
| `interactive-guide` | `interactive.integralmedia.com.au` | Enhanced feature version |

#### **Vercel Configuration**
```json
{
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

### **Alternative Deployment Options**

#### **Netlify Branch Deploys**
- **Main Site**: Deploy from `main` branch
- **Branch Previews**: Automatic deploy previews for `simplified-guide` and `interactive-guide`
- **Custom Domains**: Configure different domains for each branch

#### **GitHub Pages Multiple Repositories**
Create separate repositories if needed:
- `team-guide` (main)
- `team-guide-simplified` 
- `team-guide-interactive`

---

## 📊 Content Management Strategy

### **Shared Content Updates**

When updating content that applies to all versions:

1. **Make changes on `main` branch first**
2. **Test thoroughly**
3. **Merge to other branches**
4. **Adapt content as needed** for simplified/interactive versions

### **Version-Specific Content**

#### **Simplified Guide Adaptations**
- **Reduce content complexity** while maintaining essential information
- **Focus on daily operations** and core procedures
- **Simplify language** and reduce technical detail
- **Streamline navigation** to essential sections only

#### **Interactive Guide Enhancements**
- **Add interactive elements** (progress tracking, task completion)
- **Implement advanced features** (search, filtering, personalization)
- **Enhanced feedback systems** with real-time responses
- **Collaboration tools** for team coordination

### **EmailJS Configuration Management**

Each branch can use different EmailJS templates:

```javascript
// Branch-specific configurations
const CONFIG = {
    main: {
        serviceId: 'service_p2fplrx',
        templateId: 'template_35rncws'  // Main version
    },
    simplified: {
        serviceId: 'service_p2fplrx', 
        templateId: 'template_simple'   // Simplified feedback
    },
    interactive: {
        serviceId: 'service_p2fplrx',
        templateId: 'template_enhanced' // Advanced feedback
    }
};
```

---

## 🔧 Development Best Practices

### **Branch Naming Convention**
- **`main`**: Primary comprehensive version
- **`simplified-guide`**: Streamlined version
- **`interactive-guide`**: Enhanced feature version
- **`feature/branch-name`**: Feature branches for specific improvements

### **Commit Message Format**
```
Update [branch-name]: [brief description]

- Specific change 1
- Specific change 2
- Specific change 3

🤖 Generated with Claude Code

Co-Authored-By: Claude <noreply@anthropic.com>
```

### **Code Organization**

#### **Shared Components**
Keep these consistent across all branches:
- **CSS custom properties** (colors, fonts, spacing)
- **Base component structure** (focus-area, section-summary)
- **Navigation patterns**
- **Mobile responsive framework**

#### **Branch-Specific Files**
These can differ between branches:
- **Content text** and complexity level
- **Feature implementations**
- **JavaScript functionality**
- **EmailJS template IDs**

---

## 📈 Maintenance Workflow

### **Regular Maintenance Tasks**

#### **Weekly**
- [ ] **Check all branch deployments** are working
- [ ] **Test feedback systems** on each version
- [ ] **Review branch synchronization** for shared updates

#### **Monthly**  
- [ ] **Merge main improvements** to other branches
- [ ] **Update version-specific content** as needed
- [ ] **Check deployment URLs** and custom domains
- [ ] **Review analytics** for each version (if implemented)

#### **Quarterly**
- [ ] **Full content review** across all versions
- [ ] **Performance optimization** for each branch
- [ ] **Documentation updates** and style guide reviews
- [ ] **User feedback analysis** from all versions

### **Troubleshooting Common Issues**

#### **Merge Conflicts**
```bash
# View differences between branches
git diff main..simplified-guide

# Interactive merge resolution
git mergetool
```

#### **Branch Divergence**
```bash
# See how branches have diverged
git log --oneline --graph --all

# Find common ancestor
git merge-base main simplified-guide
```

#### **Deployment Issues**
- **Check branch-specific configurations**
- **Verify EmailJS template IDs**
- **Test mobile responsiveness** on each version
- **Confirm custom domain DNS settings**

---

## 🎯 Future Enhancement Strategy

### **Planned Improvements**

#### **Simplified Guide**
- [ ] **Checklist-based interface** for daily tasks
- [ ] **Progressive disclosure** of advanced topics
- [ ] **Quick action buttons** for common procedures
- [ ] **Simplified feedback system** with basic ratings

#### **Interactive Guide**  
- [ ] **Real-time team collaboration** features
- [ ] **Advanced search and filtering**
- [ ] **Personal dashboard** with task tracking
- [ ] **Integration with external tools** (Slack, project management)
- [ ] **Analytics and usage tracking**
- [ ] **Customizable interface** and dark mode

#### **All Versions**
- [ ] **Progressive Web App** features for offline access
- [ ] **Multi-language support** for international teams
- [ ] **Advanced accessibility** features
- [ ] **Integration with company systems**

---

## 📞 Support & Documentation

### **Branch-Specific Documentation**
- **README.md**: Updated for each branch's specific features
- **CLAUDE.md**: Development notes adapted for each version
- **STYLE-GUIDE.md**: Shared across all branches
- **ARCHITECTURE.md**: Technical documentation for all versions
- **DEPLOYMENT.md**: Deployment instructions for multi-branch setup

### **Getting Help**
- **Repository Issues**: Use GitHub issues with branch labels
- **Development Questions**: Tag issues with branch name
- **Feature Requests**: Specify which version(s) the request applies to

---

**Last Updated**: 2025-07-24  
**Branch Strategy**: Multi-version parallel development  
**Maintenance**: Regular synchronization and branch-specific updates

*Comprehensive guide for managing three distinct versions of the Integral Media Team Guide*