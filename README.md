# Infinity Clínica Dental Marbella

Production website for **Infinity Clínica Dental Marbella** — Dr Maryam Ashrafi's private dental clinic on Avenida Ricardo Soriano 36, Marbella.

Static HTML site. No build step. Deployed on Netlify.

## Pages

| File | Path | Purpose |
|---|---|---|
| `index.html` | `/` | Homepage — hero, services accordion, Dr Maryam, gallery, testimonials, FAQ, booking |
| `emergency-landing.html` | `/emergency` (rewrite) | Paid-search landing page for emergency-intent campaigns |
| `legal.html` | `/legal` (rewrite) | Aviso legal · privacidad · cookies (Spanish, LSSI + RGPD compliant) |

## Languages

The homepage and emergency landing support **English · Español · Svenska · فارسی**. The Imperial Iran flag (lion + sun) is used for Farsi as a custom inline SVG. Language preference is stored in `localStorage` under `idm_lang` and persists across page navigation. Farsi triggers RTL layout with floating-button mirroring.

The legal page is Spanish-only (the Aviso Legal is Spanish-law mandated; that's the binding text).

## Tech

- Static HTML, Tailwind via CDN (`https://cdn.tailwindcss.com`), Inter + Vazirmatn (Google Fonts)
- Schema.org `Dentist + MedicalBusiness + LocalBusiness` JSON-LD with real reviews, services, opening hours, languages, area-served cities (Marbella, Puerto Banús, San Pedro, Estepona, Nueva Andalucía, Benahávis, Mijas, Fuengirola)
- Spanish geo-meta (`geo.region=ES-AN`, `geo.position`, ICBM)
- Booking form wired to Netlify Forms (form name: `non-urgent-booking`). Recipient email is configured in Netlify dashboard under **Forms → Notifications**
- Instagram embeds for the before/after gallery (lazy-loaded so they don't block LCP)
- 24/7/365 emergency CTA routes to `wa.me/34659629077` with a pre-filled message

## Local preview

No build step. Serve the directory with anything:

```bash
# Python
python3 -m http.server 5180

# Node
npx http-server . -p 5180 -c-1
```

Then open `http://localhost:5180/`.

## Deploying to Netlify

`netlify.toml` is set up with:
- `publish = "."` — root of the repo is the deploy directory
- Long cache (`max-age=31536000`) on `/assets/*` (logo, photos, flag SVG)
- Always-revalidate on `*.html`
- Security headers (X-Frame-Options, Referrer-Policy, Permissions-Policy, X-Content-Type-Options)
- Pretty URLs: `/emergency` and `/legal` rewrite to their `.html` files

Connect the repo on Netlify, point `infinitydentalmarbella.com` at the Netlify site, done.

After deploy: enable **Forms → Notifications** in the Netlify dashboard so booking-form submissions email the practice.

## Things still to fill in

The Aviso Legal in `legal.html` has three intentionally-blank fields for Dr Maryam to provide before going live:

1. `Titular:` — legal name + structure (autónoma / sociedad)
2. `NIF/NIE:` — tax ID
3. `Inscripción profesional (Colegio de Dentistas):` — collegiate number

## Credits

Website by [Shiftedlabs.ai](https://shiftedlabs.ai).
