
# Ajith – AI Research Engineer & SaaS Growth Partner

A modern, SaaS-style personal portfolio website for Ajith M, showcasing AI research, product, SEO, and GTM expertise.  
Designed to feel like a premium SaaS landing page, with sections for services, case studies, freelance pricing, and contact.

Built using semantic HTML, custom CSS, and a small amount of vanilla JavaScript for navigation and animations.

---

## Features

- **Premium SaaS UI**
  - Gradient background and glassy cards inspired by modern SaaS products
  - Rounded cards, soft shadows, and pill-style buttons and badges

- **Hero Section**
  - Clear positioning as an AI Research Engineer & Architect for SaaS Growth
  - Role profile card with live role snapshot and skill chips
  - CTA buttons for “Freelance Plans” and “Case Studies”

- **Snapshot Panel**
  - High-level metrics (organic traffic, content volume, pipeline, products)
  - Structured in a responsive card with clear typography

- **Services**
  - Three core offerings:
    - AI-Powered SEO Engines  
    - Product Marketing & GTM  
    - Full-Stack Experimentation  

- **Signals Section**
  - Premium pill-style cards describing analytics and behaviour signals:
    Visitor timelines, engagement alerts, click paths, in-content attention, smart capture, and privacy-aware growth.

- **Case Studies**
  - Highlight work across:
    - Compliance SaaS (Complyance)
    - B2B SaaS SEO & content
    - Restaurant AI (SnapMenuAI)

- **Freelance Pricing**
  - Three SaaS-style plans:
    - Advisor  
    - Builder (featured)  
    - Partner (fractional leadership)

- **Contact Form**
  - Simple contact form with name, email, company, plan, and message
  - Mock submit handler (no backend) – safe for static hosting

- **Responsive Design**
  - Fully responsive layout for:
    - Desktop
    - Tablets / iPad
    - Mobile phones (including OnePlus Nord CE3–style widths)
  - Mobile navigation with slide-down menu

- **Lightweight Animations**
  - Intersection Observer–based scroll-in animations
  - No external JavaScript frameworks required

---

## Tech Stack

- **HTML5** – Semantic structure
- **CSS3** – Custom design system and layout
- **Vanilla JavaScript (ES6)** – Navigation toggle, scroll animations, and simple form handler
- **Google Fonts** – `Manrope` for typography

No build tools, bundlers, or frameworks are required. The site is completely static.

---

## Project Structure

```text
.
├── index.html      # Main page
├── styles.css      # Global styles, layout, and animations
└── script.js       # Navigation, scroll reveal, and form handling
````

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

### 2. Open in a browser

Because this is a static site, you can open it directly:

* Option 1: Double-click `index.html`
* Option 2 (recommended for development): use a simple local server

Example using Python:

```bash
# Python 3
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

---

## Customisation

### Update Personal Details

Most of the personal text is in `index.html`.

Key places to edit:

* **Hero section**

  * Headline, subheadline, and bullet metrics
  * CTAs and highlight pills

* **Role profile card**

  * Name
  * Role description
  * Skills chips
  * Short paragraph about current focus

* **Snapshot metrics**

  * Values for visitors, articles, pipeline, and products

* **Services, Signals, and Case Studies**

  * Titles, descriptions, and bullet points

* **Freelance Pricing**

  * Plan names
  * Monthly pricing
  * Features per plan

* **Contact section**

  * Helper text
  * LinkedIn URL or preferred contact method

All styling for colours, gradients, typography, and layout is defined in `styles.css`.
You can adjust:

* Brand colours in the `:root` variables
* Gradients in the `.bg` background
* Radii and shadows for cards and buttons

### Responsiveness

The layout responds using `grid` and `flex` plus media queries at:

* `max-width: 960px` – tablet / small laptop
* `max-width: 640px` – mobile

If you need to fine-tune behaviour for specific devices (e.g., OnePlus Nord CE3), adjust the breakpoints and styles in the `@media` sections at the bottom of `styles.css`.

---

## Navigation and Behaviour

### Mobile Navigation

* The hamburger toggle is wired up in `script.js`:

  ```js
  const navToggle = document.getElementById("navToggle");
  const nav = document.getElementById("nav");

  if (navToggle) {
    navToggle.addEventListener("click", () => {
      nav.classList.toggle("open");
    });
  }
  ```
* Styles for `.nav.open` are defined in the responsive section of `styles.css`.

### Scroll Animations

* Elements with the class `.fade-in` are observed by an `IntersectionObserver`.
* When they enter the viewport, the class `.visible` is added, triggering the CSS transition from opacity/translateY to fully visible.

```js
const observer = new IntersectionObserver(
  entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
        observer.unobserve(entry.target);
      }
    });
  },
  { threshold: 0.2 }
);

document.querySelectorAll(".fade-in").forEach(el => observer.observe(el));
```

### Contact Form

* The form does not send real emails. It prevents default submit, shows an alert, and resets:

```js
const form = document.querySelector(".contact-form");
if (form) {
  form.addEventListener("submit", e => {
    e.preventDefault();
    alert("Thank you for reaching out. I’ll get back to you shortly.");
    form.reset();
  });
}
```

To hook this into a real backend, replace this handler with your API call or third-party form service.

---

## Deployment

Because this is a fully static site, you can deploy it to many providers:

### GitHub Pages

1. Commit and push your code to GitHub.
2. In the repository settings, go to **Pages**.
3. Choose:

   * Source: `Deploy from a branch`
   * Branch: `main` (or `master`)
   * Folder: `/root` (if using the top-level files)
4. Save – GitHub will build and provide a public URL.

### Other Options

* Netlify
* Vercel
* Cloudflare Pages
* Any static hosting provider (S3, etc.)

Simply point the host to your repository or upload the static files.

---

## Roadmap / Ideas

Potential enhancements for future versions:

* Dark mode toggle
* Blog/Articles page powered by Markdown or a headless CMS
* Analytics integration (Plausible, Umami, GA4, etc.)
* Real contact/backlog integration via an API
* Additional pages for projects, talks, or publications

---

## License

You can use this structure and code as a base for your own portfolio.
If you reuse it, consider attributing the original structure and design inspiration to this repository.

```
