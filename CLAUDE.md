# CLAUDE.md — Infinity Clínica Dental Marbella

## Project
Static HTML website for Dr Maryam Ashrafi's dental clinic in Marbella. Zero build step. Deployed on Netlify.

## Layout
```
infinitydental/
├── index.html              ← homepage (hero, services, gallery, FAQ, booking)
├── emergency-landing.html  ← paid-search landing page (/emergency rewrite)
├── legal.html              ← Aviso legal + privacy + cookies (Spanish-only)
├── netlify.toml            ← deploy config + pretty URLs
├── assets/                 ← logo, real Dr Maryam portrait, hero photo, flag SVG
└── README.md
```

## Tech
- Static HTML + Tailwind v3 Play CDN (`https://cdn.tailwindcss.com`)
- Inter for body/UI, Vazirmatn for Farsi (Google Fonts)
- Schema.org JSON-LD: `Dentist + MedicalBusiness + LocalBusiness`, `Person` for Dr Maryam, `WebSite`, `FAQPage`, `BreadcrumbList`
- Booking form: Netlify Forms (`data-netlify="true"`, name `non-urgent-booking`, honeypot field `bot-field`)

## Languages
Homepage + emergency landing: **English · Español · Svenska · فارسی** with localStorage persistence (`idm_lang`) and Farsi RTL handling. Legal page: Spanish only (legally binding text per LSSI).

## Brand
- Primary purple: `#76265E`
- Light purple (header bg): `#F5E9F1`
- WhatsApp green: `#25D366`
- Body text uses slate scale (`--ink-900` through `--ink-50`)
- Imperial Iran flag (lion + sun) for Farsi — `assets/flag-iran-imperial.svg` rendered via `.inline-flag` CSS at ~0.78em height to match emoji flag dimensions

## Conventions
- All asset URLs are RELATIVE (`./assets/...`). Never absolute paths starting with `/`.
- Phone numbers: `+34 952 650 530` (clinic) and `+34 659 629 077` (24/7 emergency line)
- Email: `info@infinitydentalmarbella.com`
- All emergency CTAs route to `wa.me/34659629077` with pre-filled English message
- The clinic was established in Marbella in **2018**. Dr Maryam personally has 25+ years of experience overall.
- Clinic does NOT take insurance — purely private. Don't add insurance copy.
- Clinic opens at **10:00**, closes 19:00, Mon–Sat.

## Service-card accordion
Built with native `<details>`/`<summary>` (not max-height transitions). Tailwind CDN's preflight clamps height-related properties to 0 on custom classes — using native HTML elements bypasses the cascade.

## Mobile menu
Hamburger button visible at `<lg`. Toggle is JS-driven inline `display: block/none` on the panel (also bypassing the same cascade quirk).

## Don'ts
- Don't reintroduce insurance content
- Don't change opening time from 10:00
- Don't replace the Imperial Iran flag with the current Iran flag — Dr Maryam is a monarchist and the current flag is politically charged
- Don't change the email back from `info@` to `hello@`
- Don't commit or push without explicit user instruction

## Deploy notes
Netlify auto-deploys from `main`. Booking form submissions need a recipient email configured in Netlify dashboard → Forms → Notifications.
