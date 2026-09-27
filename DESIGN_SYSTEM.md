# VitaAssist Design System

**Design Language**: ChatGPT-inspired | **Version**: 1.0 | **Last Updated**: 2026-09-27

---

## 🎨 Design Tokens - STRICT RULES

All designers and developers **MUST** use these design tokens. **No custom colors, fonts, or styles allowed outside these tokens.**

---

## 1. Text Colors

### Rule: Use ONLY semantic color names, never hex codes in components

```
PRIMARY TEXT (Default body text)
- Light mode: #0D0D0D (almost black)
- Dark mode:  #ECECEC (almost white)
Usage: Body copy, labels, descriptions

SECONDARY TEXT (Reduced emphasis)
- Light mode: #565869 (dark gray)
- Dark mode:  #ABABAB (light gray)
Usage: Helper text, metadata, timestamps, hints

TERTIARY TEXT (Subtle, low contrast)
- Light mode: #ABABAB (light gray)
- Dark mode:  #565869 (dark gray)
Usage: Disabled text, placeholders, very subtle hints

ERROR TEXT
- Light mode: #D64545 (red)
- Dark mode:  #FF6B6B (bright red)
Usage: Error messages, warnings, destructive actions

SUCCESS TEXT
- Light mode: #2E7D32 (dark green)
- Dark mode:  #4CAF50 (bright green)
Usage: Success messages, confirmations

ACCENT TEXT (Interactive, branded)
- Light mode: #10A37F (teal/green)
- Dark mode:  #10A37F (same teal)
Usage: Links, action text, brand color
```

### ✅ DO:
```jsx
<p className="text-primary">Chat message</p>
<p className="text-secondary">Last message at 3:30 PM</p>
<span className="text-error">This field is required</span>
<a className="text-accent">Learn more</a>
```

### ❌ DON'T:
```jsx
<p style={{color: '#0D0D0D'}}>Chat message</p>
<span style={{color: '#FF6B6B'}}>Error</span>
<a style={{color: '#10A37F'}}>Link</a>
```

---

## 2. Semantic Colors (Backgrounds & States)

### Rule: Backgrounds must follow semantic meaning, not arbitrary choices

```
SURFACE (Default backgrounds)
- Light mode: #FFFFFF (white)
- Dark mode:  #191919 (very dark gray)
Usage: Main page background, default surface

SURFACE-ALT (Secondary surfaces, slight contrast)
- Light mode: #F7F7F8 (off-white)
- Dark mode:  #212121 (dark gray)
Usage: Cards, sidebar, secondary sections

SURFACE-HOVER (Hover state, interactive elements)
- Light mode: #ECECF1 (light gray)
- Dark mode:  #2A2A2A (lighter dark gray)
Usage: Hover states on buttons, list items
Requirement: Apply on ALL interactive elements on :hover

SURFACE-ACTIVE (Pressed/selected state)
- Light mode: #D7D7DB (medium gray)
- Dark mode:  #404040 (medium dark gray)
Usage: Active tabs, selected items
Requirement: Apply on :active and .is-active states

BRAND-PRIMARY (Call-to-action backgrounds)
- Light mode: #10A37F (teal)
- Dark mode:  #10A37F (same teal)
Usage: Primary buttons, important CTAs
Requirement: WHITE text on this background always

BRAND-PRIMARY-HOVER
- Light mode: #0D8B6F (darker teal)
- Dark mode:  #1B7E6A (darker teal)
Usage: Primary button hover state

BRAND-SECONDARY (Secondary actions)
- Light mode: #F7F7F8 with #0D0D0D border
- Dark mode:  #212121 with #ECECEC border
Usage: Secondary buttons
Requirement: 1px solid border

BORDER-LIGHT
- Light mode: #D1D5DB (light gray)
- Dark mode:  #404040 (dark gray)
Usage: Dividers, subtle borders

BORDER-DEFAULT
- Light mode: #BDBEC3 (medium gray)
- Dark mode:  #565869 (medium gray)
Usage: Input borders, container borders

STATE-ERROR (Error backgrounds)
- Light mode: #FEE4E4 (light red)
- Dark mode:  #4A2626 (dark red)
Usage: Error state backgrounds, alert boxes

STATE-WARNING (Warning backgrounds)
- Light mode: #FFF8DC (light yellow)
- Dark mode:  #4A4226 (dark yellow)
Usage: Warning state backgrounds

STATE-SUCCESS (Success backgrounds)
- Light mode: #E8F5E9 (light green)
- Dark mode:  #2A4A2A (dark green)
Usage: Success state backgrounds

STATE-INFO (Info backgrounds)
- Light mode: #E3F2FD (light blue)
- Dark mode:  #2A3A4A (dark blue)
Usage: Info messages, notices
```

### ✅ DO:
```jsx
<div className="bg-surface">Page content</div>
<div className="bg-surface-alt">Card</div>
<button className="bg-brand-primary hover:bg-brand-primary-hover">Send</button>
<button className="bg-brand-secondary border border-default">Cancel</button>
<div className="bg-state-error">Error occurred</div>
```

### ❌ DON'T:
```jsx
<button style={{background: '#10A37F'}}>Send</button>
<div style={{background: 'linear-gradient(45deg, #10A37F, #0D8B6F)'}}>Custom gradient</div>
<input style={{borderColor: '#FF6B6B'}}>Custom border</input>
```

---

## 3. Typography (Fonts)

### Rule: Use ONLY these typefaces. No variations allowed.

```
PRIMARY TYPEFACE: Inter
- Fallback: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif
- Reason: Modern, clean, excellent at small sizes

MONOSPACE TYPEFACE: JetBrains Mono (for code) OR SF Mono (macOS)
- Fallback: 'Courier New', monospace
- Reason: Code readability, consistent width

FONT SIZES (in pixels):
  xs:  12px (help text, small labels)
  sm:  14px (secondary text, captions)
  base: 16px (body text, default)
  lg:  18px (subheadings, list titles)
  xl:  20px (section headings)
  2xl: 24px (major headings)
  3xl: 32px (page titles, hero text)

FONT WEIGHTS:
  Regular: 400 (body text)
  Medium:  500 (labels, secondary headings)
  Semibold: 600 (button text, strong emphasis)
  Bold:   700 (primary headings, strong importance)

LINE HEIGHTS:
  Tight:   1.25 (headings)
  Normal:  1.5  (body text)
  Relaxed: 1.75 (long-form content)

LETTER SPACING:
  Normal: 0 (default)
  Wide:   0.02em (titles, for breathing room)
```

### ✅ DO:
```jsx
<p className="text-base font-normal leading-normal">Regular body text</p>
<h1 className="text-3xl font-bold leading-tight">Page Title</h1>
<label className="text-sm font-semibold">Form Label</label>
<pre className="font-mono text-sm">const code = "here";</pre>
```

### ❌ DON'T:
```jsx
<p style={{fontFamily: 'Georgia', fontSize: '17px', fontWeight: '600'}}>Custom font</p>
<h1 style={{fontSize: '35px'}}>Odd size</h1>
<code style={{fontFamily: 'Arial'}}>Code block</code>
```

---

## 4. Border Radius

### Rule: Use ONLY these predefined radius values. No custom radius.

```
RADIUS SCALE:
  none:  0px   (no rounding, sharp corners)
  sm:    4px   (subtle, used on small elements)
  base:  8px   (default, most components)
  lg:    12px  (cards, larger components)
  xl:    16px  (modals, larger surfaces)
  2xl:   20px  (hero sections, emphasized surfaces)
  full:  9999px (circles, pills)

USAGE GUIDELINES:
  - Input fields, buttons:        8px (base)
  - Cards, containers:            12px (lg)
  - Modals, dialogs:              12px (lg)
  - Avatar images:                full (circular)
  - Badge pills:                  full (rounded pill)
  - Large surfaces:               16px (xl)
  - Toggle switches:              full (rounded)
```

### ✅ DO:
```jsx
<button className="rounded-base">Click me</button>
<div className="rounded-lg">Card</div>
<img className="rounded-full w-10 h-10" src="avatar.jpg" />
<span className="rounded-full px-3 py-1 bg-state-info">Badge</span>
```

### ❌ DON'T:
```jsx
<button style={{borderRadius: '6px'}}>Custom radius</button>
<div style={{borderRadius: '50%'}}>Avatar</div>
<input style={{borderRadius: '10px'}} />
```

---

## 5. Shadows (Elevation)

### Rule: Use elevation levels ONLY. No custom box-shadows.

```
SHADOW LEVELS (Elevation system):

LEVEL 0 (No shadow - flat)
  Usage: Lowest priority elements, backgrounds

LEVEL 1 (Subtle, inline elements)
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05)
  Usage: Inline buttons, small components
  Elevation: Minimal, sits on surface

LEVEL 2 (Small depth - default for interactive elements)
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1)
  Usage: Buttons, input fields, small cards
  Elevation: Slight hover/interaction

LEVEL 3 (Medium depth - containers)
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15)
  Usage: Cards, dropdowns, small modals
  Elevation: Clear separation from background

LEVEL 4 (High depth - modals/popovers)
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2)
  Usage: Modals, large popovers, important overlays
  Elevation: Prominent, attracts attention

LEVEL 5 (Maximum depth - maximum priority)
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.25)
  Usage: Full-screen modals, maximum priority overlays
  Elevation: Maximum visual hierarchy

DARK MODE ADJUSTMENT:
  All shadows increase opacity by 20% (add 0.2)
  Example: 0 2px 4px rgba(0, 0, 0, 0.3) [instead of 0.1]
```

### ✅ DO:
```jsx
<button className="shadow-2">Standard button</button>
<div className="shadow-3">Card component</div>
<div className="shadow-4">Modal overlay</div>
<div className="shadow-1">Inline badge</div>
```

### ❌ DON'T:
```jsx
<button style={{boxShadow: '0 2px 5px rgba(0,0,0,0.15)'}}>Custom shadow</button>
<div style={{boxShadow: '0 0 15px #10A37F'}}>Colored shadow</div>
<div style={{boxShadow: 'inset 0 2px 4px rgba(0,0,0,0.1)'}}>Inset shadow</div>
```

---

## 6. Motion & Animation

### Rule: Animations must follow strict timing and easing. No arbitrary animations.

```
ANIMATION DURATIONS (milliseconds):

Fast:     150ms  (micro-interactions: button hover, icon change)
Normal:   250ms  (standard transitions: fade in, slide)
Slow:     350ms  (prominent transitions: modal appear, large movements)
Very Slow: 500ms (only for critical user attention transitions)

Restriction: No animations > 500ms without explicit PO approval

EASING FUNCTIONS (cubic-bezier):

Ease-in-out (default):
  cubic-bezier(0.4, 0, 0.2, 1)
  Usage: Most UI transitions (recommended default)

Ease-out (smooth landing):
  cubic-bezier(0.0, 0, 0.2, 1)
  Usage: Appearance animations (fade in, scale up)
  Why: Elements arrive smoothly without bouncing

Ease-in (smooth departure):
  cubic-bezier(0.4, 0, 1, 1)
  Usage: Disappearance animations (fade out, scale down)
  Why: Elements leave smoothly without bouncing

Linear:
  linear
  Usage: ONLY for continuous rotations (spinners, loaders)
  Never use for other transitions

ANIMATION USE CASES:

Button hover:
  - Duration: 150ms
  - Easing: ease-out
  - What moves: background-color, transform (scale 1.02)

Link/text hover:
  - Duration: 150ms
  - Easing: ease-out
  - What moves: color, text-decoration

Page transition (fade in):
  - Duration: 250ms
  - Easing: ease-out
  - What moves: opacity
  - Applied to: New page on load

Modal appear:
  - Duration: 250ms
  - Easing: ease-out
  - What moves: opacity, transform (scale 0.9 → 1)
  - Animation: Backdrop fades in, modal scales up

Chat message appear:
  - Duration: 250ms
  - Easing: ease-out
  - What moves: opacity, transform (translateY -10px → 0)
  - Effect: Message slides up slightly as it fades in

Loading spinner:
  - Duration: 1000ms (full rotation)
  - Easing: linear
  - What moves: transform (rotate 360deg)
  - Repeat: infinite

ANIMATIONS FORBIDDEN:

❌ NO bouncing (ease-in-back, ease-out-back)
❌ NO elastic effects
❌ NO animations > 500ms without approval
❌ NO animated gradients (performance)
❌ NO overlapping animations on same element > 3
❌ NO auto-playing animations on page load (except spinner)
```

### ✅ DO:
```jsx
<button 
  className="transition-all duration-150 ease-out hover:scale-102"
  style={{
    transition: 'all 150ms cubic-bezier(0.0, 0, 0.2, 1)'
  }}
>
  Hover me
</button>

<div
  className="animate-fade-in"
  style={{
    animation: 'fadeIn 250ms cubic-bezier(0.0, 0, 0.2, 1) forwards'
  }}
>
  Fading in...
</div>

<div
  className="animate-spin"
  style={{
    animation: 'spin 1000ms linear infinite'
  }}
>
  Loading...
</div>
```

### ❌ DON'T:
```jsx
<button 
  style={{
    transition: 'all 300ms ease-in-out, transform 200ms cubic-bezier(.68,-0.55,.265,1.55)'
  }}
>
  Don't: conflicting durations & bounce effect
</button>

<div style={{animation: 'fadeIn 1s ease-in-out'}}>
  Don't: 1s is too slow
</div>

<div style={{animation: 'rotate 1000ms ease-in forwards, scale 500ms ease-out forwards'}}>
  Don't: conflicting durations
</div>
```

---

## 7. Component-Specific Rules

### Buttons

```
PRIMARY BUTTON:
  Background: brand-primary (#10A37F)
  Text color: #FFFFFF (always white)
  Border: none
  Radius: rounded-base (8px)
  Shadow: shadow-2
  Padding: 10px 16px (height: 40px)
  Font: font-semibold, text-base
  Hover: bg-brand-primary-hover, shadow-3, scale 1.02
  Active: bg-brand-primary-hover, shadow-2
  Disabled: opacity-50, cursor-not-allowed
  Animation: 150ms ease-out

SECONDARY BUTTON:
  Background: brand-secondary (light surface with border)
  Text color: text-primary
  Border: 1px solid border-default
  Radius: rounded-base (8px)
  Shadow: shadow-1
  Padding: 10px 16px (height: 40px)
  Font: font-medium, text-base
  Hover: bg-surface-hover, shadow-2
  Active: bg-surface-active
  Animation: 150ms ease-out

DANGER BUTTON:
  Background: state-error (#D64545)
  Text color: #FFFFFF (white)
  Border: none
  Hover: darker shade of red
  Used for: Delete, logout, destructive actions
  Requires: Confirmation dialog before action

GHOST BUTTON (Icon-only):
  Background: transparent
  Text color: text-primary
  Border: none
  Radius: rounded-base
  Hover: bg-surface-hover
  Shadow: none
  Animation: 150ms ease-out
```

### Input Fields

```
Text Input / Textarea:
  Background: surface-alt
  Border: 1px solid border-default
  Border radius: rounded-base (8px)
  Padding: 10px 12px
  Font: text-base, font-normal
  Text color: text-primary
  Placeholder: text-tertiary
  
  Focus state:
    Border: 2px solid brand-primary
    Shadow: shadow-2
    Outline: none
    Padding adjusted: 9px 11px (to account for 2px border)
  
  Error state:
    Border: 2px solid state-error (#D64545)
    Background: state-error with low opacity

  Disabled state:
    Background: surface with opacity-50
    Text color: text-tertiary
    Cursor: not-allowed
    Border: 1px solid border-light

  Animation on focus: 150ms ease-out
```

### Cards

```
Card Container:
  Background: surface-alt
  Border: 1px solid border-light
  Radius: rounded-lg (12px)
  Shadow: shadow-3
  Padding: 16px
  
  Hover: shadow-4, scale 1.01 (optional, for clickable cards)
  Animation: 250ms ease-out
  
  Dark mode: darker surface-alt
```

### Chat Message

```
USER MESSAGE:
  Background: brand-primary (#10A37F)
  Text color: #FFFFFF (white)
  Radius: rounded-lg (12px)
  Max-width: 80% of container (mobile: 90%)
  Padding: 12px 16px
  Margin: 8px 0
  Alignment: right-aligned
  Animation: slideUp 250ms ease-out

AI MESSAGE:
  Background: surface-alt
  Text color: text-primary
  Radius: rounded-lg (12px)
  Max-width: 90% of container
  Padding: 12px 16px
  Margin: 8px 0
  Alignment: left-aligned
  Border: 1px solid border-light
  Animation: slideUp 250ms ease-out
```

### Modals

```
Modal Backdrop:
  Background: rgba(0, 0, 0, 0.5)
  Animation: fadeIn 250ms ease-out

Modal Container:
  Background: surface
  Border radius: rounded-lg (12px)
  Shadow: shadow-4
  Max-width: 90% (mobile), 600px (desktop)
  Animation: scaleUp 250ms ease-out
  Padding: 24px

Modal Header:
  Font: text-2xl, font-bold
  Color: text-primary
  Padding-bottom: 16px
  Border-bottom: 1px solid border-light

Modal Body:
  Padding: 16px 0
  Font: text-base, font-normal

Modal Footer:
  Padding-top: 16px
  Border-top: 1px solid border-light
  Display: flex, gap-2
  Buttons: usually (Cancel - secondary, Confirm - primary)
```

---

## 8. Implementation Checklist

### For Every Component Created:

- [ ] Uses ONLY colors from design tokens (no hex #xxx directly in JSX)
- [ ] Uses ONLY font sizes from scale (12, 14, 16, 18, 20, 24, 32px)
- [ ] Uses ONLY border-radius from scale (0, 4, 8, 12, 16, 20, 9999px)
- [ ] Uses ONLY shadows from elevation levels (0-5)
- [ ] Animations use ONLY allowed durations (150, 250, 350, 500ms)
- [ ] Animations use ONLY allowed easing (ease-out, ease-in, ease-in-out, linear)
- [ ] Hover states defined for all interactive elements
- [ ] Active states defined for buttons/inputs
- [ ] Disabled states defined for interactive elements
- [ ] Dark mode colors applied (test in dark mode)
- [ ] Mobile responsive (no fixed widths, use %)
- [ ] Accessibility: color contrast > 4.5:1 (WCAG AA)
- [ ] Accessibility: proper semantic HTML (button vs div, label for input)
- [ ] Tested on: Chrome, Firefox, Safari, Mobile Safari
- [ ] No console errors or warnings

---

## 9. Code Organization

### Tailwind CSS Setup (Recommended)

Create `tailwind.config.js`:

```js
module.exports = {
  theme: {
    colors: {
      // Text Colors
      primary: '#0D0D0D',
      secondary: '#565869',
      tertiary: '#ABABAB',
      error: '#D64545',
      success: '#2E7D32',
      accent: '#10A37F',
      
      // Semantic Colors
      white: '#FFFFFF',
      surface: '#FFFFFF',
      'surface-alt': '#F7F7F8',
      'surface-hover': '#ECECF1',
      'surface-active': '#D7D7DB',
      
      // Borders
      'border-light': '#D1D5DB',
      'border-default': '#BDBEC3',
      
      // States
      'state-error': '#FEE4E4',
      'state-warning': '#FFF8DC',
      'state-success': '#E8F5E9',
      'state-info': '#E3F2FD',
      
      // Brand
      'brand-primary': '#10A37F',
      'brand-primary-hover': '#0D8B6F',
    },
    fontSize: {
      xs: '12px',
      sm: '14px',
      base: '16px',
      lg: '18px',
      xl: '20px',
      '2xl': '24px',
      '3xl': '32px',
    },
    borderRadius: {
      none: '0px',
      sm: '4px',
      base: '8px',
      lg: '12px',
      xl: '16px',
      '2xl': '20px',
      full: '9999px',
    },
    boxShadow: {
      '1': '0 1px 2px rgba(0, 0, 0, 0.05)',
      '2': '0 2px 4px rgba(0, 0, 0, 0.1)',
      '3': '0 4px 8px rgba(0, 0, 0, 0.15)',
      '4': '0 8px 16px rgba(0, 0, 0, 0.2)',
      '5': '0 12px 24px rgba(0, 0, 0, 0.25)',
    },
    transitionDuration: {
      150: '150ms',
      250: '250ms',
      350: '350ms',
      500: '500ms',
    },
    transitionTimingFunction: {
      'ease-out': 'cubic-bezier(0.0, 0, 0.2, 1)',
      'ease-in': 'cubic-bezier(0.4, 0, 1, 1)',
      'ease-in-out': 'cubic-bezier(0.4, 0, 0.2, 1)',
    },
  },
  darkMode: 'class', // For dark mode support
};
```

### CSS Variables (Alternative)

```css
:root {
  /* Text Colors - Light Mode */
  --color-text-primary: #0D0D0D;
  --color-text-secondary: #565869;
  --color-text-tertiary: #ABABAB;
  --color-text-error: #D64545;
  --color-text-success: #2E7D32;
  --color-text-accent: #10A37F;

  /* Backgrounds - Light Mode */
  --color-surface: #FFFFFF;
  --color-surface-alt: #F7F7F8;
  --color-surface-hover: #ECECF1;
  --color-surface-active: #D7D7DB;

  /* Borders */
  --color-border-light: #D1D5DB;
  --color-border-default: #BDBEC3;

  /* Shadows */
  --shadow-1: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-2: 0 2px 4px rgba(0, 0, 0, 0.1);
  --shadow-3: 0 4px 8px rgba(0, 0, 0, 0.15);
  --shadow-4: 0 8px 16px rgba(0, 0, 0, 0.2);
  --shadow-5: 0 12px 24px rgba(0, 0, 0, 0.25);

  /* Animations */
  --transition-fast: 150ms cubic-bezier(0.0, 0, 0.2, 1);
  --transition-normal: 250ms cubic-bezier(0.4, 0, 0.2, 1);
  --transition-slow: 350ms cubic-bezier(0.4, 0, 0.2, 1);
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-text-primary: #ECECEC;
    --color-text-secondary: #ABABAB;
    --color-text-tertiary: #565869;
    --color-surface: #191919;
    --color-surface-alt: #212121;
    --color-surface-hover: #2A2A2A;
    --color-surface-active: #404040;
    --color-border-light: #404040;
    --color-border-default: #565869;
    /* Shadows increase opacity by 20% in dark mode */
    --shadow-1: 0 1px 2px rgba(0, 0, 0, 0.25);
    --shadow-2: 0 2px 4px rgba(0, 0, 0, 0.3);
    --shadow-3: 0 4px 8px rgba(0, 0, 0, 0.35);
    --shadow-4: 0 8px 16px rgba(0, 0, 0, 0.4);
    --shadow-5: 0 12px 24px rgba(0, 0, 0, 0.45);
  }
}

/* Usage */
.button-primary {
  background-color: var(--color-brand-primary);
  color: white;
  border-radius: 8px;
  box-shadow: var(--shadow-2);
  transition: all var(--transition-fast);
}

.button-primary:hover {
  box-shadow: var(--shadow-3);
  transform: scale(1.02);
}
```

---

## 10. Design System Violations & Penalties

**When you see a violation:**

1. **Minor** (using custom size like 15px instead of 16px):
   - Log it in code review
   - Request fix before merge

2. **Medium** (custom color or shadow):
   - Code review BLOCKS merge
   - Dev must refactor to use design tokens

3. **Critical** (unauthorized animation, custom font):
   - Security/performance concern
   - Must be discussed with PO
   - May require architectural change

**All violations go in a shared tracker for team accountability.**

---

## 11. Questions & Escalation

**"Can I use a custom color that's not in tokens?"**
→ No. Request PO to add it to design tokens if needed.

**"The design token doesn't match Figma, what do I do?"**
→ This file is the source of truth. Sync Figma to match this.

**"Can I make an animation longer than 500ms?"**
→ Only with explicit PO approval (document in PR).

**"What if the component needs a different corner radius?"**
→ Use the closest token. No custom values.

---

## References

- Figma Design File: [Link to Figma]
- Component Library: /src/components
- Design Tokens: /src/tokens.js or tailwind.config.js
- Approved Icons: [Link to icon set]

---

**Last Updated**: 2026-09-27 | **Next Review**: 2026-10-27
