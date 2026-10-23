# Angels Display Solutions — Website Plan

## Scope and implementation approach

Build a lightweight static website using semantic HTML, modular CSS, and vanilla JavaScript so a non-developer can replace images, captions, placeholder company facts, products, prices, and contact details from clearly labeled data sections. The site will run from a small Node static server on port 3000 and use the browser History API only where helpful; the homepage and gallery will be distinct routes with a shared shell.

The site will have two page experiences:

- `/` — editorial homepage with a controllable hero carousel, service highlights, About Us, expandable services, gallery preview, featured project placeholders, Why Us? placeholders, contact form presentation, and footer.
- `/gallery.html` — dedicated gallery plus lightbox controls, with a discreet link into the storefront prototype.

A storefront drawer/page section will be accessible from the persistent Shop control without changing the requested primary nav. Product content will live in one JavaScript configuration object, and cart state will remain front-end only in memory/localStorage. Checkout will be explicitly labeled as a prototype placeholder and will never collect card details.

The supplied `img ref.jpeg` will be reused as the brand artwork in the footer and as the source for a dark black-and-gold brand treatment; it will not be replaced by an invented logo. Temporary display-related images will use replaceable remote image URLs grouped in `src/content.js`. All placeholder business facts will be visibly prefixed with `[EDITABLE PLACEHOLDER]` in the UI and source comments.

## Design direction

### Three candidate directions

- **Quiet Luxury Editorial** (0.06): cream paper, blackened espresso, gold linework, asymmetrical editorial compositions, restrained motion.
- **Gallery Atelier** (0.07): museum-like whitespace, image-led navigation, small catalog labels, almost no ornament.
- **Neo-Art-Deco Workshop** (0.05): dark framing, geometric gold dividers, stronger contrast, more graphic UI moments.

### Chosen direction: Quiet Luxury Editorial

**Design Movement:** Quiet luxury editorial / contemporary atelier, with a dark-and-gold identity drawn from Angels Display Solutions artwork.

**Core Principles:** spacious and composed; tactile warmth; editorial asymmetry; every interaction should feel like opening a case or turning a page.

**Color Philosophy:** one continuous family of warm beige, milk, and slightly deeper sand tones keeps the entire page calm and cohesive. Subtle borders, texture, and restrained shadows separate components without deep color blocks. Muted antique gold remains a small accent for rules, numerals, focus rings, and calls to action.

**Layout Paradigm:** alternating wide image fields, offset captions, and staggered service/product compositions instead of repeated centered cards. Sections use a vertical rhythm and occasional off-grid overlaps to make the page feel art-directed without sacrificing scanability.

**Signature Elements:** a translucent beige glass-morphism header with soft blur and a thin border; thin antique-gold rules with tiny diamond markers; editorial eyebrow labels and image frames that reveal with a directional wipe and a slight scale shift.

**Interaction Philosophy:** controls are quiet but explicit. Hover and focus states expose the gold system; expandable service cards disclose content inline; the hero carousel provides pause, arrows, indicators, and touch gestures without relying on autoplay.

**Animation:** use transform/clip-path reveals and short directional transitions (350–650ms) rather than generic fades. Pause non-essential motion when hovered/focused and disable or reduce movement under `prefers-reduced-motion: reduce`.

**Typography System:** Cormorant Garamond for display headings and large numerals; Inter for body copy, labels, navigation, forms, and product metadata. Large headlines use tight tracking and fluid `clamp()` sizing. Body copy stays between 1rem and 1.1rem with generous line height.

**Brand Essence:** a considered visual merchandising partner for jewelry retailers, turning product presentation into an atmosphere. Personality: poised, tactile, exacting.

**Brand Voice:** concise, sensory, confident without invented claims. Example lines: “The room is part of the jewel.” “Built around the way your collection needs to be seen.”

**Wordmark & Logo:** use the supplied Angels Display Solutions artwork, contained in a black field with gold accents; never recreate the wordmark in a substitute font.

**Signature Brand Color:** `#C8A451`, a muted antique gold pulled from the supplied artwork and reserved for rules, active states, and key accents.

## Project structure

```text
angelsdisplay/
├── index.html              # Homepage shell and all homepage sections
├── gallery.html            # Separate gallery route and storefront entry point
├── src/
│   ├── styles.css          # Tokens, responsive layout, components, motion/accessibility
│   ├── content.js          # Replaceable image, project, service, product, and contact data
│   └── app.js              # Shared navigation, carousel, gallery, lightbox, cart, forms
├── assets/
│   └── angels-logo.jpeg    # Supplied brand artwork copied into project assets
├── public/
│   └── manus-routes.json   # Homepage and gallery route manifest
├── package.json            # Minimal static-server scripts
├── app.config.ts           # Project logo metadata
├── plan.md
└── TODO.md
```

## Build workflow

1. Create the modular static files, route manifest, project metadata, and copied brand asset.
2. Register host-managed JavaScript/CSS/HTML diagnostics before the first application-code batch.
3. Start the port-3000 static server and verify both routes plus `/manus-routes.json` over HTTP.
4. Use a read-only review pass against this plan and the brief, fix any confirmed gaps, and capture visual previews only if needed for a concrete layout issue.
5. Commit the finished files to the canonical `main` branch for a Manus checkpoint. Publication remains separate and will only be done if explicitly requested or already authorized by the project’s existing auto-publish setting.
