# Suloyal International — Website

A full 7-page marketing website for Suloyal International, built from the
provided site map, homepage/about/solutions/products/global-reach/why-suloyal/
contact copy, and the Suloyal logo. Plain HTML/CSS/JS — no build step, no
framework, no dependencies to install.

## What's inside

```
suloyal-website/
├── index.html            Home
├── about.html             About Us (story, timeline, team, founder, offices)
├── solutions.html         Cross-border B2C / B2B bulk trading / customized logistics
├── products.html          Product categories + sourcing process
├── global-reach.html      Route-network map, regions, European hub
├── why-suloyal.html       Supplier network, quality, logistics, technology, advantage
├── contact.html           Enquiry form + direct contact channels
├── css/
│   └── styles.css         Design tokens + all component styles
├── js/
│   ├── main.js            Nav toggle, scroll-reveal animation, form handling
│   └── footer.js          Shared footer (injected on every page)
└── assets/
    └── logo.png           Suloyal logo (as supplied)
```

## Opening it in Visual Studio / VS Code

1. Unzip the folder and open it in VS Code (`File → Open Folder…`).
2. Install the **Live Server** extension (by Ritwick Dey) if you don't have
   it already.
3. Right-click `index.html` → **Open with Live Server**. The site opens at
   `http://127.0.0.1:5500/index.html` with hot-reload.

You can also just double-click `index.html` to open it straight in a browser
— everything on the page works without a server, since the footer is
injected with plain JavaScript (no `fetch`, so no CORS issues from `file://`).

## Images

Every photo on the site is a real, freely-licensed stock photograph from
Unsplash (no AI-generated imagery), loaded directly from Unsplash's CDN —
so there's nothing to download, and no attribution is required under the
Unsplash License. If you'd rather host the images yourself:

1. Download each photo you want to keep from unsplash.com.
2. Drop it into `assets/images/`.
3. Update the matching `<img src="...">` / `background-image:url(...)` in
   the HTML to point at `assets/images/your-file.jpg`.

## The enquiry form (contact.html)

The form on the Contact page is fully styled and validates client-side, but
it does **not** send anywhere yet — there's no backend in a static site.
Before you publish, wire it up to one of:

- **Formspree / Getform / Basin** — add their endpoint to the `<form>`'s
  `action` attribute and remove the `preventDefault()` call in
  `js/main.js` (search for `#enquiry-form`).
- **A serverless function** (Netlify Forms, Vercel, AWS Lambda) — Netlify
  Forms in particular just needs a `data-netlify="true"` attribute added
  to the `<form>` tag if you deploy there.
- **mailto fallback** — for something quick, you can change the form
  `action` to `mailto:sherry@ugoodshunter.com` (this opens the visitor's
  email client instead of submitting silently).

## Colors, type & design notes

- **Green** (`#1e7a1e` / `#0c2410`) — sampled directly from the Suloyal
  logo.
- **Gold** (`#c6a24a`) — a muted brass accent standing in for trade routes,
  manifests and waybill stamps; used sparingly for eyebrows, stat numbers
  and the route-line map.
- **Fraunces** (display serif) + **Inter** (body) + **IBM Plex Mono**
  (data/labels — stat numbers, eyebrows, the timeline and the network map)
  — the mono face is used deliberately to evoke a shipping manifest.
- The dotted route-map on the Home and Global Reach pages is hand-built
  SVG (no map library / no external map tiles), animating its route lines
  in on scroll. It reflects the real regions in the brief (Europe, North
  America, Africa, Southeast Asia) rather than a generic globe graphic.
- All section order, copy and structure follow the supplied site map,
  homepage copy, about copy, solutions copy, products copy, global reach
  copy, why-Suloyal copy and contact copy documents.

## Editing content

Since there's no templating engine, shared markup (header nav + footer) is
duplicated at the top of each HTML file, and the footer is injected by
`js/footer.js`. If you rename a page or add a new one:

1. Copy the `<header>` block from any existing page.
2. Keep `<footer class="site-footer" id="site-footer-include"></footer>`
   and the two `<script>` tags at the bottom of `<body>`.
3. Add a matching `<li><a href="your-page.html">Your Page</a></li>` to the
   `.nav-links` list on every page (including the new one).

## Still to do before launch

- Add the founder's real photograph and biography on `about.html` (a
  placeholder monogram card is used for now).
- Swap the placeholder `href="#"` social links in the footer for real
  LinkedIn / WhatsApp / TikTok URLs.
- Wire up the contact form (see above).
- Add a real favicon set (currently reuses `assets/logo.png`).
