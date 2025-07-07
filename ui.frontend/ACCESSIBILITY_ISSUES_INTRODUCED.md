# Accessibility Issues Introduced for Demonstration

This document outlines the intentional accessibility violations that have been added to the WKND template for demonstration and testing purposes.

## 🚨 Color Contrast Issues

### Location: `ui.frontend/src/main/webpack/site/elements.scss`
- **Body text**: Changed to `#888888` on `#f0f0f0` background (poor contrast ratio)
- **Headings**: Changed to `#999999` (insufficient contrast)
- **Links**: Changed to `#aaaaaa` with hover state `#cccccc` (very poor contrast)
- **Paragraph text**: Reduced font size to `12px` with line-height `1.2` (hard to read)

### Location: `ui.frontend/src/main/webpack/components/button/scss/styles/_default.scss`
- **Default buttons**: Light gray background `#dddddd` with light gray text `#aaaaaa`
- **Primary buttons**: Light yellow background `#ffff99` with white text (poor contrast)
- **Secondary buttons**: Light gray `#e0e0e0` with very light gray text `#cccccc`

### Location: `ui.frontend/src/main/webpack/components/navigation/scss/styles/_nav-header.scss`
- **Navigation links**: Changed to `#b0b0b0` with hover `#d0d0d0`
- **Active navigation**: Yellow background `#ffff99` with white text

## 🎯 Focus Management Issues

### Location: Multiple files
- **Global focus removal**: All elements have `outline: none` removing focus indicators
- **Links**: No visible focus state
- **Buttons**: No focus indicators
- **Form elements**: No focus styling

### Location: `ui.frontend/src/main/webpack/components/navigation/navigation.js`
- **Programmatic focus removal**: JavaScript actively removes focus from elements
- **Mobile navigation**: Missing proper keyboard navigation support
- **No focus trap**: Modal navigation doesn't trap focus

## 📏 Touch Target Issues

### Location: `ui.frontend/src/main/webpack/components/button/scss/styles/_default.scss`
- **Button size**: Reduced to `20px` height and `30px` minimum width (too small for touch)
- **Font size**: Reduced to `10px` (too small)
- **Padding**: Reduced to `0.2rem 0.5rem` (insufficient touch area)

### Location: `ui.frontend/src/main/webpack/site/accessibility-issues.scss`
- **Accordion buttons**: `18px` height, `20px` width (too small)
- **Carousel indicators**: `8px` x `8px` (too small for interaction)
- **Search buttons**: `20px` x `20px` (too small)

## 📝 Form Accessibility Issues

### Location: `ui.frontend/src/main/webpack/components/form/text/scss/styles/_default.scss`
- **Input fields**: Poor contrast `#999999` text on `#f8f8f8` background
- **Labels**: Light gray color `#aaaaaa` with small font `10px`
- **Placeholder text**: Very light `#dddddd` (nearly invisible)
- **Error messages**: Light color `#ffaaaa` with tiny font `9px`
- **Focus states**: No visible focus indicators

## 🏗️ Structural Issues

### Location: `ui.frontend/src/main/webpack/site/accessibility-issues.scss`
- **Heading hierarchy**: All headings forced to same size `14px`
- **Heading contrast**: All headings use `#999999` color
- **Link identification**: No underlines, poor color contrast
- **Skip links**: Hidden improperly (never become visible)

## 🖼️ Media and Content Issues

### Location: `ui.frontend/src/main/webpack/site/accessibility-issues.scss`
- **Images**: No visual indicators for missing alt text
- **Tables**: Poor contrast for headers and cells
- **Table structure**: Headers not properly differentiated

## 🔍 Search and Navigation Issues

### Location: `ui.frontend/src/main/webpack/site/accessibility-issues.scss`
- **Search input**: Poor contrast and tiny font size
- **Search button**: Too small and poor contrast
- **Navigation**: Missing proper ARIA attributes

### Location: `ui.frontend/src/main/webpack/components/navigation/navigation.js`
- **Mobile navigation**: Missing ARIA labels and roles
- **Keyboard navigation**: No keyboard event handling
- **Logo links**: Remove aria-label attributes

## 🎛️ Interactive Elements

### Location: `ui.frontend/src/main/webpack/site/accessibility-issues.scss`
- **Modal dialogs**: No focus management
- **Carousel controls**: Too small and poor contrast
- **Interactive elements**: No hover or focus feedback

## 🎨 Visual Design Issues

### Location: Multiple files
- **Line height**: Reduced to create cramped text
- **Font sizes**: Many elements using 9px-11px fonts (too small)
- **Spacing**: Insufficient padding and margins throughout
- **Color differentiation**: Poor contrast ratios across the board

## Testing These Issues

To test these accessibility issues:

1. **Automated testing**: Use tools like axe-core, Lighthouse, or Pa11y
2. **Manual testing**: Try navigating with keyboard only
3. **Screen reader testing**: Test with NVDA, JAWS, or VoiceOver
4. **Color contrast**: Use tools like WebAIM's contrast checker
5. **Mobile testing**: Test touch targets on mobile devices

## Fixing These Issues

Each issue is commented in the code with `/* ACCESSIBILITY ISSUE: */` for easy identification and removal. To fix:

1. Remove the accessibility-issues.scss import from main.scss
2. Revert changes to elements.scss, button styles, and navigation styles
3. Implement proper focus management in JavaScript
4. Add proper ARIA attributes and semantic HTML
5. Ensure sufficient color contrast ratios (4.5:1 for normal text, 3:1 for large text)
6. Make touch targets at least 44px x 44px
7. Implement proper keyboard navigation 