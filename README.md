# CSS Glowing Button

A small collection of lightweight CSS styles for creating modern, customizable glowing buttons. No JavaScript required — just HTML + CSS. Ideal for landing pages, CTAs, and UI components that need a subtle neon-like glow.

![Button preview](https://i3.ytimg.com/vi/b_8fHNIHFk4/maxresdefault.jpg)

Features
- Pure CSS (no JS).
- Easy to drop-in and customize with CSS variables.
- Hover/focus animations and accessible reduced-motion support.
- Small, framework-agnostic, works with button and anchor elements.

## Live demo
Try the [live demo](https://i3.ytimg.com/vi/b_8fHNIHFk4/maxresdefault.jpg)

Add this HTML to preview a button:

```html
<button class="glow-btn">Click me</button>
```

Basic CSS
Drop this into your stylesheet (or copy into a demo file):

```css
/* Basic glowing button */
.glow-btn {
  --glow-color: #7afcff;
  --glow-size: 12px;
  padding: 0.6rem 1.2rem;
  font-size: 1rem;
  border-radius: 8px;
  border: none;
  color: #fff;
  background: linear-gradient(90deg, #111827, #374151);
  cursor: pointer;
  position: relative;
  box-shadow: 0 0 var(--glow-size) rgba(122, 252, 255, 0.35);
  transition: transform 200ms ease, box-shadow 200ms ease;
}

/* soft lift + stronger glow on hover */
.glow-btn:hover,
.glow-btn:focus {
  transform: translateY(-3px);
  box-shadow: 0 0 calc(var(--glow-size) * 1.6) rgba(122, 252, 255, 0.6);
}

/* decorative blurred glow layer */
.glow-btn::before {
  content: "";
  position: absolute;
  inset: -10px;
  border-radius: inherit;
  background: radial-gradient(circle at center, var(--glow-color), transparent 35%);
  filter: blur(12px);
  opacity: 0.6;
  z-index: -1;
  transition: transform 300ms ease, opacity 200ms ease;
}

.glow-btn:hover::before {
  transform: scale(1.05);
  opacity: 1;
}

/* accessible focus style */
.glow-btn:focus {
  outline: 3px solid rgba(255, 255, 255, 0.06);
  outline-offset: 2px;
}

/* reduce motion preference */
@media (prefers-reduced-motion: reduce) {
  .glow-btn,
  .glow-btn::before {
    transition: none;
    transform: none;
  }
}
```

Usage
- Copy the CSS into your stylesheet or include it in a component.
- Add class="glow-btn" to any <button> or <a> element.
- Override the variables or properties to change appearance.

Customization
- --glow-color — change the glow hue (e.g., #ff6b6b, #7afcff).
- --glow-size — controls blur radius and shadow intensity.
- Background — replace the background gradient with your brand gradient or solid color.
- Border-radius, padding, font-size — adjust to fit your design system.

Examples
- Different colors:

```css
.green { --glow-color: #5efc82; background: linear-gradient(90deg,#0b3d0b,#166a16); color: #fff;}
.pink  { --glow-color: #ff6bcb; background: linear-gradient(90deg,#2b0f1f,#5b1133); color: #fff;}
```

- Link style:

```html
<a href="#" class="glow-btn" role="button">Learn more</a>
```

Accessibility notes
- Focus states are included for keyboard users.
- The code respects prefers-reduced-motion; users who disable motion will not see animations.
- Ensure sufficient contrast between foreground text and the button background for readability.

Browser support
Modern evergreen browsers (Chrome, Edge, Firefox, Safari). Uses CSS variables and basic pseudo-elements — for older browsers, you can provide fallback styles.
