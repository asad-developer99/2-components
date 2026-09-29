# DermExcel — Interactive UI Showcase

A two-page front-end project exploring a **clay / skeuomorphic design language** with rich motion and interaction. It pairs a scroll-driven 3D photo gallery landing page with a tactile hardware-style control dashboard. No build step and no framework are required.

| Page | File | Description |
| --- | --- | --- |
| **Gallery** | `index.html` | Dark landing page with a 3D Fibonacci-sphere gallery that rotates as you scroll |
| **Dashboard** | `index2.html` | Carbon-and-orange control panel with draggable knobs, faders, toggles, and tabs |

A floating button in the bottom-right corner of each page switches between the two.

---

## Features

### Gallery page (`index.html`)
- **3D Fibonacci sphere layout** — 24 image cards distributed evenly on a sphere using CSS 3D transforms.
- **Scroll-driven rotation** — GSAP ScrollTrigger scrubs the sphere through two full rotations across a 300vh scroll area.
- **Dynamic captions** — title and description cross-fade as scroll progress changes.
- **Focus highlighting** — cards near the active index switch from muted grayscale to full color.
- **Parallax constellation** — scattered cards in the closing "Start Your Journey" section drift on scroll.
- **Clay UI components** — chunky buttons, soft inset shadows, and a subtle grid overlay.
- **Responsive** — smaller sphere radius and card size on screens under 768px.

### Dashboard page (`index2.html`)
- **Rotary knobs** — a large main dial and a secondary jog dial, both draggable to any angle.
- **Vertical faders** — two draggable sliders with a glowing liquid fill.
- **Clay buttons** — toggleable power and transport buttons with an inset "pressed" state.
- **Segmented tabs** — single-select tab groups.
- **Slide toggles, checkboxes, and radios** — with orange glow active states.
- **Responsive** — the lower control grid stacks on screens under 540px.

---

## Tech Stack

- **HTML5**, **CSS3** (custom properties, 3D transforms, gradients, layered shadows)
- **Vanilla JavaScript** (ES6)
- **[GSAP 3.12.2](https://gsap.com/)** with the **ScrollTrigger** plugin, loaded from cdnjs (gallery page only)

---

## Project Structure

```
.
├── index.html      # Gallery / landing page
├── style.css       # Styles for the gallery page
├── script.js       # Sphere generation, GSAP scroll animation, captions
├── index2.html     # Control dashboard page
├── style2.css      # Styles for the dashboard page
├── script2.js      # Knob, slider, toggle, and tab interactions
└── README.md
```

---

## Getting Started

No installation is needed.

**Option 1 — Open directly**

Open `index.html` in a modern browser.

**Option 2 — Local server (recommended)**

```bash
# Python
python3 -m http.server 8000

# or Node
npx serve .
```

Then visit `http://localhost:8000`.

> **Note:** The gallery page needs an internet connection to load GSAP from the CDN and the product images from Shopify's CDN.

---

## Customization

### Gallery images and captions (`script.js`)
- Replace the URLs in the `images` array to use your own photos.
- Edit the `textContent` array to change the captions that appear during scrolling.
- Change the `.slice(0, 24)` value to adjust the number of cards on the sphere.
- Adjust the `radius` constant (`380` desktop, `200` mobile) to change the sphere size.
- Change `rotateY: 360 * 2` in the ScrollTrigger tween to control the number of rotations.

### Theme colors
Both stylesheets expose design tokens in `:root`:

- `style.css` — `--bg-dark`, `--text-main`, `--text-muted`, `--clay-base`, and related clay shadow variables.
- `style2.css` — `--panel-bg`, `--clay-base`, `--clay-top`, `--milled-dark`, `--orange-glow`, `--orange-liquid`.

Changing `--orange-glow` and `--orange-liquid` re-themes the whole dashboard accent color.

### Initial dashboard values (`script2.js`)
- Knob starting angles: `setupKnobRotation(element, initialRotation)`
- Fader starting positions: `setupVerticalSlider(thumbId, fillId, initialPercentage)`

---

## Browser Support

Tested design targets are current versions of Chrome, Edge, Firefox, and Safari. The gallery relies on `preserve-3d`, `backdrop-filter`, and `position: sticky`, which older browsers may not support.

---

## Known Limitations

- Dashboard knobs and faders respond to **mouse events only**. Touch and pointer support are not yet implemented.
- Dashboard controls are visual and do not drive any audio or application state.
- Gallery images are hotlinked from an external CDN and will not display if those URLs change or go offline.
- Dashboard page has no keyboard or screen-reader support for the custom controls yet.

## Roadmap Ideas

- Switch to Pointer Events for touch and stylus support.
- Add keyboard controls and ARIA roles to knobs, sliders, and toggles.
- Bundle local image assets and self-host GSAP for offline use.
- Persist dashboard state with `localStorage`.

---

## License

Add your preferred license here (for example, MIT) before publishing.