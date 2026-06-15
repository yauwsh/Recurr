# Recurr

**Find $50–$200/month you're already losing.**

Recurr is a free subscription audit tool that maps every recurring charge, flags dormant and overpriced bills, and provides step-by-step negotiation playbooks with real phone numbers and word-for-word scripts to lower your bills.

---

## What it does

- **Free audit** — Add your subscriptions and bills. Recurr automatically flags dormant charges, high-cost services, and bills with negotiation leverage.
- **Negotiation playbooks** — Step-by-step scripts, real phone numbers, and Know Your Rights sections for Internet/Cable, Mobile, Insurance, Medical Bills, Streaming/SaaS, and Gym memberships.
- **Savings tracker** — A running "money saved" counter tracks your wins over time.

---

## Revenue model

- Free: subscription listing, dashboard, and audit
- $39 one-time: unlocks all 6 negotiation playbooks
- Payment via Stripe (integration in progress)

---

## Tech stack

- Vanilla HTML/CSS/JS with React 18 (via CDN — no build step required)
- localStorage for persistence — no backend, no database
- Single-file architecture (`recurr.html`)

---

## Getting started

No build tools required. Just open the file:

```bash
open recurr.html
```

Or serve it locally:

```bash
npx serve .
```

Then open `http://localhost:3000` in your browser.

---

## Deployment

### Netlify (recommended)

1. Drag and drop the repo folder at [netlify.com/drop](https://netlify.com/drop)
2. Or connect this GitHub repo in the Netlify dashboard for auto-deploy on push

### Vercel

```bash
npx vercel
```

### GitHub Pages

1. Go to **Settings → Pages**
2. Set source to **main branch / root**
3. Rename `recurr.html` to `index.html`
4. Your site will be live at `https://yourusername.github.io/recurr`

---

## Stripe integration (TODO)

The upgrade button currently shows a placeholder. To wire up payments:

1. Create a [Stripe Payment Link](https://stripe.com/payments/payment-links) for $39
2. Replace the `alert()` stub in the `UpgradeModal` component with your Payment Link URL
3. On successful payment, set `recurr_paid: true` in localStorage

For a more robust flow (webhook-based unlock, email delivery):
- Set up a Stripe webhook to `POST /api/webhook`
- Verify the `checkout.session.completed` event
- Return a signed token or session flag to the client

---

## Project structure

```
recurr/
├── recurr.html     # Entire app — landing, dashboard, audit, playbooks
└── README.md
```

---

## Roadmap

- [ ] Stripe payment integration
- [ ] Email delivery of playbooks on purchase
- [ ] CSV/bank import for automatic subscription detection
- [ ] Quarterly re-audit reminder emails
- [ ] Shareable savings card for word-of-mouth growth
- [ ] Convert to Vite + React for component-based architecture

---

## License

MIT
