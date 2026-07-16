# Quick Crave Snacks — Website

A conversion-focused marketing site for **Quick Crave Snacks LLC**, a family-owned vending
business serving the greater Chicago area. The site is built as a **sales tool**: it's designed
to convince business owners to host a machine while building trust with everyday customers.

Plain HTML/CSS/JS — **no build step, no framework**. Open it in a browser or drop it straight
into Claude Code and start iterating.

---

## 1. What's in here

```
QuickCraveSnacks/
├── index.html          Homepage (hero, benefits, why-us, how-it-works, machines, locations, CTA)
├── about.html           Story, mission/vision/values, service area
├── machines.html         Snack / Beverage / Combo spec sheets
├── contact.html          "Get a Free Machine" lead-capture form
├── css/styles.css        All styling + brand tokens (colors, fonts)
├── js/main.js             Nav, scroll animations, form handling
├── assets/
│   ├── logo.svg           Logo (on-brand placeholder — see §3)
│   ├── favicon.svg        Browser tab icon
│   └── img/               Vending-machine illustrations (placeholders — see §3)
└── README.md              You're reading it
```

## 2. Run it / load into Claude Code

**Preview locally:** just double-click `index.html`, or serve it:

```bash
cd QuickCraveSnacks
python3 -m http.server 8000   # then open http://localhost:8000
```

**Claude Code:** open the whole `QuickCraveSnacks` folder as your project. Everything is
plain files, so you can ask Claude Code to tweak copy, colors, or add pages with no setup.

---

## 3. ⚠️ Replace the logo and machine images with your real assets

No logo file was attached in this session, so `assets/logo.svg` and `assets/favicon.svg` are
**on-brand SVG placeholders** (black rounded badge + gold lightning bolt) built to match the
site's palette. The vending-machine photos are also **SVG illustrations**, not real photos.

**To swap in your real logo:**
1. Add your file to `assets/` (e.g. `assets/logo.png`).
2. Find-and-replace `assets/logo.svg` → `assets/logo.png` across `index.html`, `about.html`,
   `machines.html`, and `contact.html` (each page references it twice: nav + footer).
3. Do the same for the favicon `<link rel="icon">` tag in each page's `<head>`.

**To swap in real machine photos**, drop your files into `assets/img/` using these exact names,
then update the matching `src="..."` in the HTML (search each file for `-machine.svg` and change
the extension):

| Replace this placeholder            | With your photo named        |
|-------------------------------------|------------------------------|
| `assets/img/hero-machine.svg`       | `hero-machine.jpg` (or .png) |
| `assets/img/snack-machine.svg`      | `snack-machine.jpg`          |
| `assets/img/beverage-machine.svg`   | `beverage-machine.jpg`       |
| `assets/img/combo-machine.svg`      | `combo-machine.jpg`          |

In Claude Code you can just say: *"replace the machine SVGs with the .jpg photos I added to
assets/img"* or *"replace the placeholder logo with the file I added to assets/"* and it'll
update every reference. Transparent PNGs on a dark background look best for the hero.

Also confirm the **spec numbers** on `machines.html` (capacity, dimensions, selections) against
your actual vending machine models — realistic typical values were used as a starting point.

---

## 4. Make the contact form actually email you (2 minutes)

The form on `contact.html` is ready to go — it just needs a free form backend. Easiest is
**Formspree** (free tier, works on any static host):

1. Go to **https://formspree.io** and sign up with your business email.
2. Create a new form; Formspree gives you an endpoint like `https://formspree.io/f/abcdwxyz`.
3. In `contact.html`, find this line and replace `YOUR_FORM_ID` with your ID:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST" data-demo="true">
   ```
4. Delete the ` data-demo="true"` part of that same tag. That's it — submissions now email you.

(Alternatives that work the same way: Getform, Web3Forms, or a Google Form embed.)

---

## 5. Set up your business email (linked to Gmail)

An email address can't be created from a website file — it has to be set up with a provider, and
it requires owning your domain first. Here are the two real paths. **Step 1 is the same for both:**

**Step 1 — Get the domain.** Register `quickcravesnacks.com` (~$12/yr at Namecheap, Cloudflare,
Google Domains/Squarespace, GoDaddy, etc.). The whole site already uses
`hello@quickcravesnacks.com` as the address, so once you own the domain everything matches.

**Path A — Google Workspace (recommended, most professional):**
- Sign up at **workspace.google.com** (~$7/user/month). Use "Quick Crave Snacks" as the business.
- It walks you through verifying your domain and creates `hello@quickcravesnacks.com` as a full
  Gmail-powered inbox with your logo, Calendar, Drive, etc.
- You log in exactly like Gmail — it *is* Gmail, just on your own domain.

**Path B — Free-ish: use your existing Gmail (no monthly fee):**
- Most registrars include **free email forwarding**. Set `hello@quickcravesnacks.com` to forward
  to your personal Gmail — now you *receive* business email in Gmail.
- To also *send* as `hello@quickcravesnacks.com`: in Gmail go to
  **Settings → Accounts and Import → "Send mail as" → Add another email address**, enter the
  business address, and follow the SMTP steps (your registrar or a service like ImprovMX/Zoho
  Mail free tier provides these). Now replies come from your business address, inside your normal
  Gmail.

Path A is cleaner and looks more established to the businesses you're pitching; Path B is free
and fine to start. Either way, keep the address consistent with the site (`hello@…`).

> Want a different address (e.g. `info@`, `sales@`, `nathan@`)? Do a find-and-replace for
> `hello@quickcravesnacks.com` across all four HTML files, or ask Claude Code to do it.

Also update the **phone number** — the site uses a placeholder `(312) 555-0137`. Find-and-replace
it (and `+13125550137` in the `tel:` links) with your real number.

---

## 6. Put it online (free)

Any static host works. Since you already use GitHub, easiest options:

- **GitHub Pages:** push this repo → Settings → Pages → deploy from `main`. Free.
- **Netlify / Vercel / Cloudflare Pages:** drag-and-drop the folder or connect the repo. Free,
  and they make it easy to point your `quickcravesnacks.com` domain at the site.

---

## 7. Brand notes (for future edits)

- **Colors** live at the top of `css/styles.css` under `:root`:
  - Black `#0B0C0E`, brand gold `#FFCC00`, deep amber `#E89C00` (all from your logo)
  - Fresh mint `#21D19F` for "healthy / go" accents, warm paper `#F6F5F1` for light sections
- **Fonts:** Archivo (headlines), Hanken Grotesk (body), Space Mono (the little A1/B2 "vend
  codes" — a nod to machine selection buttons). Loaded from Google Fonts in each page's `<head>`.
- The little **A1 / B2 / V3** labels on cards are intentional — they echo vending-machine
  selection codes. Remove them anytime if you'd rather keep it plain.

---

Questions or changes? Open the folder in Claude Code and describe what you want — it's all
editable plain text.
