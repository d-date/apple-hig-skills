---
name: apple-app-icon
description: Use when designing, creating, reviewing, or exporting an Apple app icon, preparing icon layers for Icon Composer or an Xcode asset catalog, or checking an icon against Apple's Human Interface Guidelines. Covers iOS, iPadOS, macOS, tvOS, visionOS, and watchOS — layered Liquid Glass icons, shape and masking, design rules, system effects, dark/clear/tinted appearances, alternate icons, and size/color-space specs.
---

# Apple App Icons (HIG)

Source: https://developer.apple.com/design/human-interface-guidelines/app-icons (last change: June 8, 2026 — "Refined guidance for Liquid Glass").
To refresh, fetch the raw page data: `https://developer.apple.com/tutorials/data/design/human-interface-guidelines/app-icons.json` (the HTML page is JS-rendered).

## Specifications

| Platform | Layout shape | Shape after masking | Layout size | Style | Appearances |
|---|---|---|---|---|---|
| iOS, iPadOS, macOS | Square | Rounded rectangle (square) | 1024x1024 px | Layered | Default, dark, clear light, clear dark, tinted light, tinted dark |
| tvOS | Rectangle (landscape) | Rounded rectangle | 800x480 px | Layered (parallax, 2–5 layers) | N/A |
| visionOS | Square | Circular | 1024x1024 px | Layered (3D, background + 1–2 layers) | N/A |
| watchOS | Square | Circular | 1088x1088 px | Layered | N/A |

- Provide one size; the system scales down for Settings, notifications, etc.
- Color spaces: sRGB, Gray Gamma 2.2, Display P3 (not visionOS).

## Tooling

- **iOS / iPadOS / macOS / watchOS**: draw foreground layers in your design tool → import into **Icon Composer** (ships with Xcode). There you set the background (solid or gradient), place layers, tune Liquid Glass (specular, refraction, translucency), annotate default/dark/mono variants, preview across system versions, and export for Xcode.
- **tvOS / visionOS**: add layers to an **image stack** in the Xcode asset catalog. Preview parallax with Parallax Previewer / Parallax Exporter from Apple Design Resources.
- Production templates with placement grids: Apple Design Resources.

## Layers

- Foreground layers: **clearly defined edges** — no soft/feathered edges (breaks system highlights/shadows).
- **Vary opacity** across foreground layers for depth. Import fully opaque layers and adjust transparency inside Icon Composer.
- Background: stands out *and* emphasizes the foreground. Prefer Icon Composer's solid/gradient; an imported background must be **full-bleed and opaque**.
- Formats: **vector (SVG/PDF)** preferred; outline all artwork and convert text to outlines. Use **PNG** for mesh gradients and raster art.

## Shape and masking

- Provide **unmasked** layers: square (iOS/iPadOS/macOS/visionOS/watchOS), rectangle (tvOS). The system applies rounded corners or circular masks. Pre-masked layers break specular highlights and produce jagged edges.
- **Center primary content** so corner rounding / circular masks don't truncate it — especially visionOS and watchOS.

## Design

- Simplicity: one core concept, minimal shapes. Fine detail looks busy under system shadows/highlights and vanishes at small sizes.
- Simple background (solid or gradient); no need to fill the canvas.
- Consistent design across every platform the app supports.
- Filled, overlapping shapes (with transparency/blur) give depth.
- Text only when essential to the brand. A mnemonic letter is OK; avoid words like "Watch", "Play", "New", "For visionOS". tvOS: put text on the top layer so parallax doesn't crop it.
- Illustrations over photos. No replicated standard UI components or screenshots.
- Avoid extremely thin lines and sharp corners.
- Never depict Apple hardware (copyrighted).

## Visual effects

- **Let the system do effects.** Don't bake in specular highlights, inter-layer drop shadows, bevels, blurs, or glows — they conflict with dynamic system effects. If you must, test in Icon Composer, a simulated device in Device Hub, or on hardware.
- Group layers (in Icon Composer or your design tool) to apply effects at group level; groups expose extra Liquid Glass controls.

## Appearances (iOS, iPadOS, macOS)

Users choose default, dark, clear, or tinted. Unprovided variants are auto-generated.

- Keep core features identical across all appearances; don't swap elements per variant.
- Dark/clear/tinted are progressively more subdued — still must be visible, legible, recognizable next to system icons and widgets.
- Derive dark from the light icon: complementary colors, no overly bright imagery; colored backgrounds give the best contrast in dark.
- **Alternate icons** (iOS, iPadOS, tvOS, compatible visionOS apps): must stay tied to your content and not look like another app. On iOS/iPadOS each alternate needs its own dark, clear, and tinted variants. All icons go through App Review.

## Platform specifics

- **tvOS**: keep a safe zone; focus scaling/motion crops edges, foreground layers more than background. Safe zone varies with size, depth, and motion.
- **visionOS**: no holes/concave shapes in the background layer — system shadows and highlights make them pop out instead of recede.
- **watchOS**: no black background; lighten it so the icon doesn't disappear into the display.

## Review checklist

When reviewing an icon or asset set, check each and report violations with the rule above:

1. Correct canvas size and shape for each target platform; single master size provided.
2. Layers are unmasked, square/rectangular, hard-edged; background full-bleed and opaque.
3. Vector (outlined text) or PNG; supported color space.
4. Primary content centered within the template grid; tvOS safe zone respected.
5. Simple concept, few shapes, no thin lines, no UI screenshots, no Apple hardware; flag photos as a weaker choice than illustrations.
6. No text unless essential; no call-to-action or context words.
7. No baked-in shadows, highlights, bevels, blurs, or glows (or justified and tested).
8. Dark / clear / tinted variants keep the same features and stay legible (iOS/iPadOS/macOS); alternate icons include their own variants.
9. Platform rules: visionOS no concave background shapes; watchOS no black background.
10. Visual consistency across all supported platforms.
