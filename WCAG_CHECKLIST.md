# WCAG 2.1 Accessibility Audit Checklist

This checklist helps verify that your portfolio meets WCAG 2.1 Level AA and AAA accessibility standards.

## Perceivable

### Text Alternatives (Level A & AA)
- [ ] All images have descriptive alt text
- [ ] Alt text describes image purpose, not just "image of..."
- [ ] Decorative images have empty alt attributes (`alt=""`)
- [ ] Profile image has appropriate description
- [ ] Product/project images have detailed alt text

### Adaptable Content (Level A & AA)
- [ ] Page content doesn't rely on color alone
- [ ] Information isn't presented in a specific orientation only
- [ ] CSS custom properties used for colors
- [ ] Headings properly hierarchical (H1, H2, H3, no skips)
- [ ] Logical reading order in HTML

### Distinguishable (Level AA & AAA)
- [ ] Text contrast ratio is 7:1 (WCAG AAA)
- [ ] Large text contrast is 4.5:1 minimum
- [ ] Links are distinguishable (underlined or color + style)
- [ ] Focus indicators are visible (3px outline)
- [ ] Text can be resized up to 200% without breaking layout
- [ ] Colors in combination aren't sole means of information

## Operable

### Keyboard Accessible (Level A & AA)
- [ ] All functionality available via keyboard
- [ ] Tab order follows visual layout
- [ ] No keyboard trap exists
- [ ] Tabindex not used in excess (only if necessary)
- [ ] Focus order makes sense (logical progression)
- [ ] Skip link appears on Tab press

### Enough Time (Level A)
- [ ] No auto-refreshing content
- [ ] No time-dependent actions
- [ ] Animations can be stopped if longer than 5 seconds

### Seizure Prevention (Level A)
- [ ] No content flashes more than 3 times per second
- [ ] Animations respect prefers-reduced-motion

### Navigable (Level A & AA)
- [ ] Navigation is consistent across pages
- [ ] Page has a clear title (in `<title>` tag)
- [ ] Focus indicator clearly visible
- [ ] Skip link present and functional
- [ ] Navigation menu properly labeled
- [ ] Current page indicated in navigation

## Understandable

### Readable (Level A & AA)
- [ ] Language specified in `<html lang="en">`
- [ ] Font size at least 16px (or scaled appropriately)
- [ ] Line height at least 1.4x (1.6 used here)
- [ ] Letter spacing preserved
- [ ] Word spacing preserved
- [ ] Text not fully justified

### Predictable (Level A & AA)
- [ ] Navigation consistent across pages
- [ ] Form fields behave predictably
- [ ] No context change on focus
- [ ] No context change on user interaction
- [ ] Buttons and links clearly identifiable

### Input Assistance (Level A & AA)
- [ ] Form labels clearly associated with inputs
- [ ] Form errors identified
- [ ] Error messages suggest corrections
- [ ] Required fields marked clearly
- [ ] Form validation provides helpful messages
- [ ] Confirm action before submission (if critical)

## Robust

### Compatible (Level A & AA)
- [ ] Valid HTML5 doctype
- [ ] Valid HTML5 structure
- [ ] No duplicate IDs
- [ ] Proper nesting of elements
- [ ] Correct use of ARIA attributes
- [ ] ARIA attributes valid (no invalid role/property combinations)

### ARIA Implementation (Level A & AA)
- [ ] ARIA labels describe purpose clearly
- [ ] `aria-label` used appropriately
- [ ] `aria-labelledby` properly linked
- [ ] `aria-describedby` for extra information
- [ ] `aria-required` on required fields
- [ ] `aria-current="page"` on current nav item
- [ ] `role` attributes valid and appropriate
- [ ] No redundant ARIA (e.g., aria-label on labeled input)

## Page-Specific Checklists

### Home Page (index.html)
- [ ] Hero section is meaningful and clear
- [ ] Skills section items are distinct
- [ ] All headings present and hierarchical
- [ ] Navigation works with keyboard
- [ ] Skip link works

### About Page (about.html)
- [ ] Profile image has descriptive alt text
- [ ] Profile information is organized with headings
- [ ] Experience section uses semantic structure
- [ ] Figure/figcaption used for profile image

### Projects Page (projects.html)
- [ ] Projects listed with clear descriptions
- [ ] Project links have descriptive aria-labels
- [ ] Each project is distinguishable
- [ ] Collection structure is clear

### Contact Page (contact.html)
- [ ] All form fields have labels
- [ ] Required fields marked
- [ ] Required indicator visible and labeled
- [ ] Form validation messages are clear
- [ ] Error messages appear in alert role
- [ ] Helper text is accessible
- [ ] Submit and Reset buttons both present
- [ ] Tab order makes sense (top to bottom)

## Form Accessibility Detailed

### Form Field Labels
- [ ] Every input has associated label
- [ ] Label `for` matches input `id`
- [ ] Label text is descriptive
- [ ] Label doesn't contain form instructions

### Form Field Types
- [ ] `<input type="text">` for text
- [ ] `<input type="email">` for email
- [ ] `<input type="tel">` for phone (if used)
- [ ] `<textarea>` for longer text
- [ ] `<select>` for dropdowns
- [ ] Appropriate input types used

### Form Validation
- [ ] Required fields marked `aria-required="true"`
- [ ] Format requirements explained in helper text
- [ ] Error messages in `role="alert"`
- [ ] Errors identified to user and field
- [ ] Suggestions provided for correction

## Testing Instructions

### Automated Testing
1. **WAVE Browser Extension**:
   - Install from webaim.org/wave/extension/
   - Run on each page
   - Fix all errors (red)
   - Review warnings (yellow)

2. **axe DevTools**:
   - Install from deque.com/axe/devtools/
   - Run scan on each page
   - Fix all violations
   - Review best practices

3. **Lighthouse**:
   - Open DevTools (F12)
   - Click Lighthouse tab
   - Run accessibility audit
   - Target 100/100 score

### Manual Testing

#### Keyboard Navigation
1. Open each page in browser
2. Press Tab repeatedly through page
3. Verify focus indicator visible
4. Test Enter on links/buttons
5. Test form submission via keyboard
6. Verify skip link works

#### Screen Reader Testing (NVDA - Windows)
1. Download NVDA from nvaccess.org
2. Start NVDA (Ctrl + Alt + N)
3. Open browser
4. Use NVDA key (Insert) + arrow keys to navigate
5. Verify all content is announced
6. Check headings are announced
7. Check form labels are announced
8. Verify links have descriptive text

#### Color Contrast
1. Use WebAIM Color Contrast Checker
2. Test all text colors against background
3. Test link colors against background
4. Ensure 7:1 ratio (AAA) or minimum 4.5:1 (AA)
5. Check focus indicator colors

#### Responsive Design
1. Open each page on mobile (< 480px)
2. Verify layout adapts
3. Verify text readable without zoom
4. Verify buttons/links large enough to tap
5. Test landscape orientation

#### Dark Mode
1. Open DevTools (F12)
2. Click three dots → More tools → Rendering
3. Find "Emulate CSS media feature prefers-color-scheme"
4. Select "dark"
5. Verify colors still have good contrast
6. Verify page is readable

#### Reduced Motion
1. Open DevTools Rendering tab
2. Find "Emulate CSS media feature prefers-reduced-motion"
3. Select "reduce"
4. Verify animations are disabled or minimal
5. Verify page is still functional

## Common Issues & Fixes

### Issue: Focus not visible
**Fix**: Check CSS has visible outline on `:focus` selector
```css
input:focus, a:focus, button:focus {
  outline: 3px solid #ffd700;
}
```

### Issue: Low color contrast
**Fix**: Use darker text or lighter background
- Test with WebAIM Color Contrast Checker
- Aim for 7:1 ratio minimum

### Issue: Missing alt text
**Fix**: Add descriptive alt to all images
```html
<img src="image.png" alt="Description of what image shows">
```

### Issue: Form labels not associated
**Fix**: Use proper label associations
```html
<label for="email">Email</label>
<input id="email" type="email">
```

### Issue: Heading hierarchy broken
**Fix**: Use H1, H2, H3 in order without skips
```html
<h1>Main Title</h1>
<h2>Section Title</h2>
<h3>Subsection</h3>
```

### Issue: No keyboard navigation
**Fix**: Don't disable tab order, ensure semantic elements
```css
/* Don't do this */
* { outline: none; }

/* Do this instead */
*:focus { outline: 3px solid color; }
```

## Resources for Testing

### Browser Extensions
- WAVE: webaim.org/wave/extension/
- axe DevTools: deque.com/axe/devtools/
- ChromeVox: Free screen reader for Chrome

### Online Tools
- WebAIM Color Contrast: webaim.org/resources/contrastchecker/
- Lighthouse: developers.google.com/web/tools/lighthouse
- WAVE Online: wave.webaim.org/
- Schema Validator: validator.schema.org/

### Screen Readers
- NVDA (Windows): nvaccess.org
- JAWS (Windows): Freedom Scientific (commercial)
- VoiceOver (Mac/iOS): Built-in
- TalkBack (Android): Built-in

## Success Criteria

✅ **All the following must pass**:
- [ ] WAVE scan shows 0 errors
- [ ] axe DevTools shows 0 violations
- [ ] Lighthouse Accessibility = 100
- [ ] Lighthouse SEO = 100
- [ ] Keyboard navigation works fully
- [ ] Screen reader announces all content
- [ ] Color contrast ≥ 7:1 (AAA)
- [ ] Focus indicators visible
- [ ] All pages tested

## Notes

Document any issues found and fixes applied:

```
Issue: _______________
Page: _______________
Fix Applied: _______________
Date: _______________
```

---

**Last Verified**: [Date]  
**Tested By**: [Name]  
**Status**: ✅ Fully Compliant
