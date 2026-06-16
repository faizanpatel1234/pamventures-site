# Pam Premium Hotel — Website

Source for **[pamventures.in](https://pamventures.in)**, the website for Pam Premium Hotel
in Vadodara. It is a static site hosted on **GitHub Pages** (the custom domain is set in
[`CNAME`](CNAME)). There is no build step — each page is a self-contained HTML file using
[Tailwind CSS](https://tailwindcss.com) via CDN.

## Pages

| File | Purpose | Audience |
| --- | --- | --- |
| [`index.html`](index.html) | Cinematic hotel landing page — hero, heritage, gallery, suites, booking and contact. | Public |
| [`menu.html`](menu.html) | Arab Ino restaurant in-room dining menu, with search, categories and dietary indicators. | Public |
| [`404.html`](404.html) | Branded "page not found" page, served automatically by GitHub Pages. | Public |
| [`dashboard.html`](dashboard.html) | Hotel operations / analytics dashboard. | Internal staff |
| [`HotelDashboard.html`](HotelDashboard.html) | Night report dashboard (revenue, tariffs, collections). | Internal staff |

The public pages link to one another: the landing page links to the menu ("Dine"), and the
menu links back to the landing page. The two dashboards are internal tools and are not linked
from the public navigation.

## Local preview

No tooling is required — open a file directly in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deployment

Pushing to the default branch publishes the site through GitHub Pages. The custom domain
`pamventures.in` is configured via the [`CNAME`](CNAME) file; do not remove it.

## Conventions

- Brand colour is gold `#C5A059` on charcoal `#0D0D0D`.
- Fonts: Cormorant Garamond (display/serif) and DM Sans (body) on the landing page;
  Playfair Display and Lato on the menu.
- Keep filenames lowercase and without spaces so they map cleanly to URLs.
