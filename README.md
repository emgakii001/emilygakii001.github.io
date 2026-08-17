[README.md](https://github.com/user-attachments/files/31135074/README.md)
# Emily Gakii — Portfolio

Finance & bookkeeping portfolio site. Plain HTML/CSS/JS, no build step, no framework, no backend — built to deploy directly on GitHub Pages.

**Status:** "Empty but Live" milestone (Week 4). The site is structured for the full content plan but only the Home and Contact pages are fully written. Other pages are intentional placeholders — see "What's a placeholder right now" below.

---

## File structure

```
/
├── index.html          Homepage — hero, problem framing, Selected Work carousel
├── about.html           placeholder
├── services.html         placeholder
├── work.html             placeholder (case study index)
├── credentials.html      placeholder
├── contact.html          fully built
├── favicon.ico
├── assets/
│   ├── css/style.css     all styles, one file, uses CSS variables for the brand tokens
│   ├── js/main.js        mobile nav toggle + active-link highlighting (vanilla JS)
│   ├── logo/              SVG brand marks (monogram, favicon, horizontal lockup)
│   └── images/projects/   put real case-study screenshots here as you add them
└── README.md
```

No page uses a templating engine, so the header/nav and footer are repeated in every HTML file. This is intentional for a beginner-maintainable static site — no build step required — but it means **if you edit the nav (e.g. add a page), you need to paste that change into every `.html` file.**

---

## What's a placeholder right now

- **About, Services, Work, Credentials** — each has the header/nav, a page title, and a dashed placeholder box. Replace the placeholder box with real content when you're ready; don't need to touch anything else on the page.
- **Selected Work carousel (homepage)** — pulls from a small JavaScript array near the bottom of `index.html` (`var projects = [...]`). To update a project card, edit that array — you don't need to touch the CSS or the carousel logic. To link a card to a real case study page once you've built one, change the disabled "View Project" button to a real `<a href="work/loan-portfolio-analysis.html">`.
- **Contact page** — email and LinkedIn are placeholders (`hello@emilygakii.com`, `linkedin.com/in/emily-gakii`). **Replace these before sharing the live link.** They're marked with `<!-- TODO -->` comments in `contact.html` and in the footer of every page.
- **About photo** — no photo is included. Add a real photograph when you build out the About page; the brief is explicit that this should never be AI-generated.

---

## Brand tokens (don't change without updating the identity kit)

Defined once at the top of `assets/css/style.css`:

| Variable | Value | Use |
|---|---|---|
| `--navy` | `#16324F` | primary brand color, headings, buttons |
| `--charcoal` | `#1F2933` | body text |
| `--soft-white` | `#F8FAFC` | background |
| `--teal` | `#2F7F7B` | accent only — used sparingly (labels, focus states, active nav underline) |

Font is **Manrope**, loaded from Google Fonts in the `<head>` of every page, falling back to Helvetica Neue / Arial. If you add a new page, copy the two `<link>` tags for `fonts.googleapis.com` / `fonts.gstatic.com` and the stylesheet `<link>` from an existing page.

---

## Adding a new case study page later

1. Duplicate `work.html` as a starting template (keeps the nav/footer consistent).
2. Follow the three-beat structure from the brief: **The Problem → What I Did → What Came From It.**
3. Drop real screenshots into `assets/images/projects/`.
4. If you have a standalone HTML dashboard, either:
   - link out to it directly ("Open Interactive Dashboard" button), or
   - embed it with an `<iframe>` if it's lightweight enough not to slow the page down.
5. Update the matching card in the homepage carousel (`index.html`) to link to the new page and swap its status badge from "Coming soon" to nothing (remove the badge span) or "Featured" if it's your strongest piece.

---

## Deploying to GitHub Pages

This site uses **relative paths everywhere**, so it works whether it's a user page or a project page — no config changes needed either way.

1. Create a GitHub repository and push this folder's contents to the `main` branch.
   - If the repo is named `your-username.github.io`, the site becomes your root domain: `https://your-username.github.io/`
   - If it's named anything else (e.g. `portfolio`), it becomes a project page: `https://your-username.github.io/portfolio/`
2. In the repository: **Settings → Pages → Build and deployment → Source → Deploy from a branch.**
3. Select branch `main`, folder `/ (root)`, and save.
4. GitHub gives you the live URL within a minute or two — open it on your phone to confirm it's reachable, which is the actual milestone for this stage.

No further configuration is needed since there's no build step.

---

## Adding a real contact form later

Currently the Contact page uses a plain `mailto:` link — no backend, nothing to break. When you're ready for an actual form:

1. Sign up for a free tier of a form backend service (e.g. Formspree).
2. Add a `<form>` in `contact.html` pointing at the endpoint they give you.
3. No other code on the site needs to change.

---

## Local preview

No build tools needed. From this folder, run any static file server, e.g.:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000` in a browser.
