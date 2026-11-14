# Grid Layout Task: CSS Animation & 3D Heart

**Student:** Jonathan Katanacho
**Student ID:** 202404295

A single-file page (`index.html`) with all HTML, CSS and JavaScript in one file. It was generated with AI from one prompt, included in [PROMPT.md](PROMPT.md).

## Features

- **Layout:** one CSS grid on `<body>` with named areas and zero wrapper `div`s. The layout holds up when the window or the menu is resized, and scrollbars appear inside the right areas.
- **Header:** drop shadow, Arabic/English toggle (switches the page to right-to-left), "Add content" (the header grows to fit), and "Clear content" (resets everything).
- **Menu:** resizable left menu, pure CSS (`resize: horizontal`).
- **CSS animation:** an SVG shape pattern that slides left in a seamless infinite loop, with the "CSS Animation" text always centered.
- **3D heart:** a human heart rendered with `<model-viewer>`. Drag to rotate, scroll to zoom.
- **Content:** a scrollable article in English and Arabic.
- **Footer:** always visible, and only under the content area.
- **Floating button:** sits on the border between the content and the footer, with a hover animation.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole page |
| `heart.glb` | Free CC0 human heart model from [Grab3D](https://grab3d.com/models/anatomy/human-heart/) |
| `PROMPT.md` | The single prompt used to generate the page |

## Run it

Open `index.html` through a local server, such as VS Code's **Live Server** extension. Opening the file directly (`file://`) blocks the 3D model from loading.
