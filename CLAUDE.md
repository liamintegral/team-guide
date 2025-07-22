# Integral Media Project - Claude Development Notes

## Project Overview
Complete team guide and resource hub for Integral Media, providing daily operational guidance and comprehensive reference materials for team members.

## Project Consolidation & Optimization Log

### Major Debloating Project (2025-07-22)
**Issue**: Project had grown to 550KB+ with massive duplication across 8 HTML files
**Symptoms**:
- 95% redundancy in team member information
- 24KB of duplicate CSS across all files
- 8 HTML files with overlapping content
- No external CSS usage despite having integral-style.css

**Root Cause**:
- Each HTML file contained complete inline CSS (4-15KB each)
- Content was duplicated across multiple files
- No centralized styling system
- Poor file organization

**Resolution Applied**:
- **CSS Consolidation**: Extracted all inline CSS to external stylesheet
- **Content Analysis**: Identified and archived redundant files
- **File Structure**: Reduced from 8 to 3 active HTML files
- **Size Reduction**: 550KB → 215KB (61% reduction)

**Files Modified**:
- Enhanced `styles/integral-style.css` with consolidated styles
- Converted all HTML files to use external CSS links
- Archived 5 redundant files to `archive-redundant-files/`
- Updated project documentation

**Current Structure**:
- `integral-media-complete-guide.html` (164KB) - Main comprehensive guide
- `documentation/industry-specific-considerations.html` (33KB) - Unique content
- `documentation/kind-kitchens-remarketing-brief.html` (18KB) - Example brief
- `styles/integral-style.css` (14KB) - Consolidated external stylesheet

---

### Bug: Content Overflow on Resource Grid (2025-07-21) - RESOLVED
**Issue**: Content overflowing horizontally causing layout problems
**Resolution**: Fixed grid layout and added to external CSS
**Status**: ✅ Resolved in CSS consolidation

---

## Development Commands

### Testing
- Open file directly in browser: `file:///Users/liamclarkin/ClaudeCode%20Projects/Integral%20Media%20Project/integral-media-complete-guide.html`
- Hard refresh to bypass cache: Cmd + Shift + R (Mac) or Ctrl + Shift + R (Windows/Linux)

### File Structure
- Main document: `integral-media-complete-guide.html`
- Documentation: `CLAUDE.md` (this file)
- Project readme: `README.md`
- Resources: `documentation/` folder