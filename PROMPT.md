# The prompt (single prompt used to generate index.html)

Build a single-file web page (`index.html`): all HTML, CSS and JavaScript in ONE file, no build step. The goal is the most efficient code possible: the fewest tags needed for the layout. Use zero wrapper `div`s: put the layout directly on `<body>` as a CSS grid with named areas, and generate repeated content (menu items, article) from small JS data arrays instead of hand-writing it.

**Layout (CSS grid on body, full viewport height, the page itself never scrolls):**
- Columns: `menu | content | content`. Rows: `header`, `top row`, `content`, `footer`.
- `header` spans the full width. `nav` (left menu) spans from under the header to the bottom of the screen. The `footer` sits only under the content area. It does NOT extend under the menu.
- Top row, side by side and equal width: a `section` with the CSS animation (left) and a `<model-viewer>` with a 3D human heart (right).
- Below them, an `article` that is the only scrollable area. Fill it with long generated content so scrolling is visible.
- Use `minmax(0, 1fr)` tracks so nothing ever overflows or overlaps. The layout must never break while the window or the menu is resized; scrollbars appear inside the right areas instead.

**Header:**
- Dark red (#a30000) bar with a drop shadow.
- Left: a white rounded logo badge with a red graduation-cap icon and the bold serif title "Training 2026".
- Right: three small text buttons with icons: "العربية" (globe), "+ Add content" (plus), "Clear content" (trash).
- "العربية" switches the whole page to Arabic and right-to-left (the menu moves to the right). The button then reads "English" and switches back.
- "Add content" adds a dynamic chip to the header each click. The header uses flex-wrap and grows to fit its content; the rest of the layout shrinks to make room.
- "Clear content" resets everything at once: removes the chips, returns to English, resets the menu width, scrolls the article to the top.

**Left menu (`nav`):**
- Light gray, resizable horizontally with pure CSS (`resize: horizontal; overflow: auto`), with a min and max width.
- 15 items, each with a small colored Lucide line icon and a label: Dashboard, HTML Editor, CSS Styles, JS Console, Components, Templates, Snippets, Projects, Live Preview, Responsive Design, Color Palette, Typography, Animations, Debugger, Settings.
- Labels don't wrap. When the menu is narrow or short, it scrolls instead of breaking.

**Animation section (this must match exactly):**
- Red diagonal gradient background (#c80000 → #8a0000).
- On top of it, a pattern of white shapes as an inline SVG data-URI tile:
  - translucent filled "leaf" shapes (rounded squares with one less-rounded corner) of different sizes and opacities
  - small outlined leaves
  - one tall outlined rounded rectangle drawn as a thick faint stroke with a thin brighter stroke inside it
- The pattern slides smoothly and continuously to the LEFT in a seamless infinite loop (linear, no jump at the loop point). Animate a `::before` layer with `transform: translateX(-tileWidth)` for performance.
- Centered white bold serif text "CSS Animation" with a dark text-shadow. It does not move and stays perfectly centered at any size.

**3D heart section:**
- Light gray (#f2f2f2) background.
- `<model-viewer src="heart.glb" camera-controls auto-rotate>` (Google model-viewer from a CDN). The heart spins continuously in a circle from the moment it loads. The user can also drag to rotate and scroll or pinch to zoom.
- `heart.glb` is the free CC0 human heart model from Grab3D (https://grab3d.com/dl/human-heart/human-heart-light.glb), placed next to index.html. If the local file fails to load, fall back to that URL.

**Article content:**
- Title "HTML, CSS & JavaScript", an intro paragraph, then one block per topic: HTML, CSS, JavaScript, The DOM, Flexbox, CSS Grid, Responsive Design, Accessibility, Performance, Git & GitHub.
- Each block: an `h3` and a paragraph with a colored square badge in front of it (HTML orange #e34c26, CSS blue #264de4, JS yellow #f7df1e with black text, others in fitting colors). Draw the badge with `::before` from a data attribute (no extra tags).
- Provide full English and Arabic versions.

**Footer:**
- Thin light bar, centered small text: "© 2026 Training 2026. All rights reserved." plus my name and student ID: Jonathan Katanacho, 202404295.

**Floating button:**
- A red circular "+" button positioned fixed so it sits exactly on the border between the content area and the footer, at the end side (right in English, left in Arabic). It is outside the normal layout.
- On hover, it grows slightly, its shadow deepens and the "+" rotates 90°. Clicking it does the same as "Add content".

**Fonts:** serif (like the reference) for the title, animation text, article and footer; sans-serif for the menu and header buttons.

Add `<meta name="author" content="Jonathan Katanacho - 202404295">`.
