# UI Effects Libraries

A curated list of open-source GitHub repos for 3D, liquid, gradient, and animated UI effects. All free, all vibe-codeable — you can drop any of these into a landing page, hero section, or microsite to get a visual treatment that takes most teams weeks to build from scratch.

## Why this list exists

By 2026, the line between "design asset" and "shippable code" collapsed. These repos give you production-grade visual effects as React components, vanilla JS, or shader code — no Figma → developer handoff required. If you're building a hero, a product showcase, or a moment of visual delight, start here.

The point of the list isn't "install all four." It's "know what's possible." The next time a brief says "we want the hero to feel alive" or "the launch needs a moment of magic," you know which repo to reach for instead of designing from scratch.

## The four standouts

### ShaderGradient

**Repo:** [github.com/ruucm/shadergradient](https://github.com/ruucm/shadergradient)

Animated, customizable gradient meshes powered by WebGL shaders. Drop into a React app, tune the controls in real time. The output looks like the kind of background you see on a well-funded SaaS hero or a Figma marketing page — but the controls are exposed so you're not stuck with the defaults.

**Use when:** You need a moving, depth-having gradient for a hero section. Static CSS gradients look flat in 2026; this gives the same surface a sense of motion and weight without going full 3D.

**Watch out for:** WebGL performance on low-end mobile. Always test on a mid-range Android before shipping to a global audience.

**License:** Check the repo before redistributing in a client project.

### liquid-logo

**Repo:** [github.com/paper-design/liquid-logo](https://github.com/paper-design/liquid-logo)

Transforms a logo or brand mark into a liquid, morphing surface — the Apple iOS 26 "liquid glass" aesthetic applied to your wordmark. By Paper Design (the team behind the paper.design platform).

**Use when:** You're presenting a brand identity and need the wordmark to feel alive — a product reveal video, a launch site, the centerpiece of a pitch deck. Pairs well with subtle music and a slow fade.

**Watch out for:** It's an animation, not an icon. Static screenshots lose what makes it special — use it only where motion plays.

**License:** Check the repo before redistributing.

### liquid-glass-js

**Repo:** [github.com/dashersw/liquid-glass-js](https://github.com/dashersw/liquid-glass-js)

A vanilla-JS implementation of the liquid-glass surface effect — distortion, refraction, soft edges — applied to any DOM element. Lighter weight than liquid-logo, no React dependency. Drop into any page.

**Use when:** You want the visual quality of an Apple-style "frosted refractive" surface without committing to a React component library. Good for buttons, modals, hero overlays, navigation bars.

**Watch out for:** Browser support. The underlying effects rely on CSS / WebGL features that may degrade on older browsers — always provide a sensible fallback.

**License:** Check the repo before redistributing.

### react-three-fiber

**Repo:** [github.com/pmndrs/react-three-fiber](https://github.com/pmndrs/react-three-fiber) (license: MIT)

The big one. React renderer for Three.js — lets you build 3D scenes declaratively, the same way you build React components. Backbone of essentially every React-based 3D UI on the web in 2026.

**Use when:** Anything 3D — product visualizations, interactive hero scenes, scroll-driven 3D storytelling, particle systems, custom material effects. Bigger commitment than the other three (you'll learn Three.js along the way), but unlocks an entire category of visual work.

**Watch out for:** Bundle size and initial-paint cost. Code-split aggressively and lazy-load the canvas. Always show a static fallback for users with prefers-reduced-motion.

**License:** MIT.

## How to use this list

1. **Pick one repo, clone it, run the example.** Screenshot the result. That screenshot becomes a reference for the next deck you build or page you design.
2. **Don't install all four at once.** Each adds bundle weight and complexity. Match the tool to the brief, not the brief to the tool.
3. **Verify the license before shipping client work.** Most are MIT or MIT-like, but always check the repo's `LICENSE` file before redistributing inside a deliverable.

## Contributing

This list grows by PR. If you've used a repo on real client work and it held up under shipping conditions — open a PR adding it with:

- The repo URL
- One paragraph on what it does and when to use it
- A note on license and any production gotchas (bundle size, browser compat, learning curve, mobile performance)

The bar is "I shipped this and it survived," not "looks cool on Twitter."

## Source

Originally compiled from a public Instagram reel circulating in 2026 highlighting the four repos above. Sourced from Shaurya's wiki notes and reshaped for this toolkit so Matt, Jamie, and anyone else doesn't have to remember where the bookmark went.
