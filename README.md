# Gemz Automate — Website

**Smart AI Automations Working 24/7 for You.**

A production-ready, 5-page static website for **Gemz Automate**, an AI automation agency for local businesses. Built with plain **HTML, CSS and vanilla JavaScript** — no frameworks, no build step. Just upload the files and go.

Domain: **Automate.GemzOnline.Com**

---

## 📁 File Structure

```
/
├── index.html          # Home
├── services.html       # Services (6 detailed services)
├── about.html          # About (story, mission, why choose us)
├── pricing.html        # Pricing (3 tiers + FAQ)
├── contact.html        # Contact (info + Web3Forms form + Calendly)
├── README.md
└── assets/
    ├── css/
    │   ├── styles.css       # Layout, components, responsive
    │   └── animations.css   # Hero animations + effects
    ├── js/
    │   └── main.js          # Nav toggle, FAQ, scroll reveal
    └── images/
        ├── logo.png         # Dark-background logo (used as favicon)
        ├── logo-light.png   # Light-theme logo (used in nav + footer)
        └── icons/           # Custom service icons (website, social, email, receptionist, voice, reputation)
```

---

## 🚀 Deploying to Hostinger

This is a static site, so deployment is simple:

1. Log in to your Hostinger control panel (hPanel).
2. Open **File Manager** and go to the `public_html` folder of your domain (`Automate.GemzOnline.Com`).
3. Upload **all files and folders** from this project into `public_html`, keeping the folder structure exactly as shown above (`assets/` must stay a folder).
4. Make sure `index.html` sits at the top level of `public_html`.
5. Visit your domain — you're live. 🎉

> Tip: You can also zip everything, upload the zip, then use "Extract" in File Manager.

---

## 🔧 Placeholder Replacement Guide

Before going live, replace every placeholder below. The fastest way is a **project-wide Find & Replace** in your code editor across all `.html` files.

| # | Find this placeholder | Replace with | Appears in |
|---|-----------------------|--------------|------------|
| 1 | `https://calendly.com/YOUR-CALENDLY-LINK` | Your real Calendly booking link | All pages (nav, CTAs, contact) |
| 2 | `YOURPHONENUMBER` | Your WhatsApp number in **international format**, digits only (e.g. `15551234567`) | All `wa.me/` links + floating button |
| 3 | `+1YOURPHONENUMBER` | Your business phone for click-to-call (e.g. `+15551234567`) | Footer + contact page `tel:` links |
| 4 | `+1 (555) 000-0000` | Your business phone as displayed text | Footer + contact page |
| 5 | `YOUR_WEB3FORMS_KEY` | Your Web3Forms access key (see below) | `contact.html` form |
| 6 | Facebook `href="#"` | Your Facebook page URL | Footer (all pages) |
| 7 | Instagram `href="#"` | Your Instagram URL | Footer (all pages) |
| 8 | LinkedIn `href="#"` | Your LinkedIn URL | Footer (all pages) |
| 9 | `[PRICE PLACEHOLDER]` | Your monthly prices for each tier | `pricing.html` |

Every placeholder in the code is marked with an HTML comment beginning `<!-- PLACEHOLDER:` so you can locate them quickly.

The email address **gemzonline2@gmail.com** is already set throughout — update it if your contact email changes.

---

### ✉️ Setting up the contact form (Web3Forms)

The contact form uses [Web3Forms](https://web3forms.com) — a free service that emails you form submissions from a static site (no backend needed).

1. Go to **https://web3forms.com** and enter your email (`gemzonline2@gmail.com`) to get a free **Access Key**.
2. Open `contact.html` and find:
   ```html
   <input type="hidden" name="access_key" value="YOUR_WEB3FORMS_KEY" />
   ```
3. Replace `YOUR_WEB3FORMS_KEY` with the key you received.
4. Submissions will now be emailed to you. Done.

---

### 📅 Embedding your live Calendly scheduler (optional)

On `contact.html` there is a Calendly section with a button link. To embed the full inline scheduler instead, find the `CALENDLY EMBED PLACEHOLDER` comment and replace that block with:

```html
<div class="calendly-inline-widget" data-url="https://calendly.com/YOUR-CALENDLY-LINK" style="min-width:320px;height:700px;"></div>
<script src="https://assets.calendly.com/assets/external/widget.js" async></script>
```

---

## 🎨 Brand Reference

| Element | Value |
|---------|-------|
| White (background) | `#FFFFFF` |
| Section Alt background (light grey) | `#F4F6FA` |
| Electric Blue (accent) | `#1E6FFF` |
| Primary text (charcoal) | `#1A2233` |
| Heading ink (navy) | `#0A0F2C` |
| Muted grey text | `#5B6676` |
| Border grey | `#E3E8F0` |
| Ice blue (icon tiles) | `#EAF1FF` |
| Headings font | Poppins |
| Body font | Inter |

All colors are defined as CSS custom properties at the top of `assets/css/styles.css` (`:root { ... }`), so you can rebrand the entire site by editing a few values.

---

## 🧩 Features

- Sticky top navigation with mobile hamburger menu
- Floating WhatsApp button on every page
- Animated hero backgrounds (moving gradient + circuit dots)
- Fully mobile responsive
- Hover glow effects on cards and buttons
- Smooth scrolling + scroll-reveal animations
- FAQ accordion on the pricing page
- Accessible, semantic HTML with `prefers-reduced-motion` support

---

© 2026 Gemz Automate. All Rights Reserved.
