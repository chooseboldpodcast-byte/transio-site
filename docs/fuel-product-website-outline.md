# Outline: Adding Fuel Reconciliation as Trasio's Second Product

**Internal planning doc — not served.** Created 2026-06-15.
**Context:** The live site (`index.html`) currently markets one product, ShiftClose, under a company-level "Physical AI for convenience retail" hero. This outlines how to add **Fuel Reconciliation** as product #2.

Grounded in: the canonical positioning ("Perception AI for retail" — the perception layer for physical AI in retail) and the Trasio brand system (the verification artifact already ships the state words `RECONCILED`, `MATCHED`, `VARIANCE DETECTED · UNRESOLVED`).

---

## Why this is a clean fit (not a bolt-on)

1. **The site is already built for it.** The hero is a *company-level* category claim; everything below is ShiftClose. The umbrella exists — we just show it now holds two products.
2. **Fuel reconciliation is the vision arc made real.** Positioning Tier 2 = "Reason: anomaly detection, what's-missing alerts, variance." The fuel product is proof the thesis is executing.
3. **Two products, two wallets.** ShiftClose sells **time** (5-minute close). Fuel sells **money** (you're paying for fuel you never received). Same motion — *perceive → reconcile → flag* — pointed at the delivery instead of the shelf.

**Thesis:** *Evolve the site from "single product under a category hero" to "two products on one perception layer," leading the fuel product with the operator's money pain (not the AI category), because the company hero already carries the category and operators convert on recovered dollars.*

**Success looks like:** a visitor understands in ~5s that Trasio has two products, self-selects by pain (time vs money), and the fuel buyer reaches a "show me what I overpaid" CTA. **Failure:** burying ShiftClose, or the home reading like two unrelated companies.

---

## 0. The one decision first — information architecture

Pick the multi-product structure. **Recommended: (B).**

- **(A) Everything on home, add a fuel section** — fastest, but home gets long and the products blur.
- **(B) Platform home + per-product pages** *(recommended)* — `/shiftclose` and `/fuelmatch`. Current deep ShiftClose content moves to `/shiftclose`; home keeps hero + a two-product split + top proof.
- **(C) Two near-separate microsites** — overkill; fractures brand + SEO.

Everything below assumes (B).

---

## 1. Positioning the fuel product

- **Company umbrella stays put:** "Perception AI for convenience retail / system of record for inventory truth." Don't touch the hero's category claim.
- **Product-level frame leads with money:** the operator proof *is* the lead on a product page. Headline direction (draft, for a copy pass — not final): *"Stop paying for fuel you never received."*
- **Unifying motion across both products: Perceive → Reconcile → Flag.** ShiftClose perceives the shelf; Fuel perceives the bill of lading. Both reconcile against the system of record and flag the variance. Reuses the exact brand vocabulary (`RECONCILED` / `MATCHED` / `VARIANCE DETECTED`).
- **Honest tension:** the "physical/perception AI" story is strongest for shelf vision; fuel's camera reads a *document* and the payoff is *financial*. Resolution — on the fuel page perception is the **mechanism**, money is the **headline**. Don't force "physical AI" as the fuel hero.
- **Name — LOCKED: Trasio FuelMatch** (decided 2026-06-15). Ties to the `MATCHED` verification state word and reads as "your delivery matched your bill." (Considered and set aside: FuelClose, DeliveryGuard.)
- **Scope of the public claim — two-way (decided 2026-06-15):** the page sells **BOL ↔ supplier invoice** reconciliation (deployable to a founding store today). The **bank/EFT (three-way) leg is intentionally OFF the public page** — Plaid isn't wired and carries the invoice-# limitation; keep it as internal roadmap until it's real.

---

## 1a. Upgrades to fold in from the FuelMatch copy draft (2026-06-15)

A second designer's full page copy added three ideas stronger than this outline had — adopt them:

1. **FuelMatch is software + SERVICE, not just a detector — the biggest upgrade.** Trasio doesn't only flag a bad load; **Trasio works the dispute with the vendor on the operator's behalf** (makes the calls/emails, verifies the charge is reversed or never collected). For time-poor owner-operators this is a far stronger value prop and a real moat — *"automation without building a back-office reconciliation team."* Reframe the product as a **managed service with software underneath** (this also unlocks value-based pricing vs. a flat tool fee).
2. **Name the three charges in operator language** (use these on the public page instead of the engine's status names):
   - **Phantom Delivery Charge** — invoiced for a load with no BOL on file *(= `missing_bol`)*. Hero example: 8,800 gal × $4.50 = **$39,600**.
   - **Volume Overbilling** — invoice gallons > BOL gallons *(= `gallons_mismatch`, invoice > BOL)*. Example: BOL 8,000 vs invoice 8,800 → 800 × $4.50 = $3,600.
   - **Price Variance** — invoice $/gal > your contract rack price *(coded but HIDDEN — off all public copy until it ships; see §5)*.
3. **Use the bank as the ticking clock, not a feature.** *"The bank auto-draft can pay the invoice before anyone checks"* creates urgency (*catch it before the draft clears*) without claiming bank reconciliation — fully compatible with the no-bank-claim decision, and it sharpens it.

Also adopt: a **calm-confidence hero** — *"Know your fuel bill is right"* — paired with the loss proof beneath it (more on-brand than a pure loss-aversion headline); an explicit **ShiftClose platform-fit** section; and **consultative CTAs** ("Talk to us about FuelMatch" / "Schedule a walkthrough").

**Keep from this outline (the draft omits it): the free Fuel Audit lead magnet** — *"send last month's deliveries, we'll show what you overpaid."* It's the strongest top-of-funnel hook **and** it's literally the managed service's first concierge touch. Make it the secondary CTA or a standalone band.

*(Honesty flags on these adopted claims live in §5.)*

---

## 2. Site structure changes

- **Nav:** `Product` → **`Products ▾`** dropdown (ShiftClose · FuelMatch). Keep `Technology · Pricing · Blog`. CTA stays "Join Founding Stores."
- **New "Two products" section** (after hero, before "Engineered for the Edge") — ready copy from the designer (price-variance language removed per the hidden-feature decision):
  - **Label:** `TWO WAYS TRASIO PROTECTS YOUR STORE`
  - **Headline:** "Every shift. Every fuel load. Covered."
  - **Subhead:** "Trasio runs on the tablets you already own — closing shifts in minutes and making sure your fuel invoices match what you actually got."
  - **Card 1 — `SHIFT MANAGEMENT` · Trasio ShiftClose:** "Close shifts in 5 minutes. AI counts inventory behind the counter, timestamps every handoff, and flags disputes automatically. No barcode guns, no nightly recount loop." → "See ShiftClose →" (`/shiftclose`)
  - **Card 2 — `FUEL RECONCILIATION` · Trasio FuelMatch:** "Scan the BOL in the app. Trasio checks it against your vendor invoice. If something doesn't match, our team contacts the vendor and works the case — so you don't have to." → "See FuelMatch →" (`/fuelmatch`)
  - **Platform one-liner under both cards:** "One platform. One login. Two protections — for the shelf behind the counter and the fuel in your tanks."
- **`/shiftclose`** — existing deep content (Sarah/Mike scenarios, three benefits, Inside ShiftClose) moves here largely as-is.
- **`/fuelmatch`** — new page (section outline in §3).
- **Pricing page** — FuelMatch shows **"Contact us"** for now (no published price), consistent with the consultative CTA; ShiftClose pricing unchanged.
- **Footer** — add Products links.

---

## 3. The `/fuelmatch` product page — section by section

Mirror the ShiftClose page *rhythm* (same family) but lead with money:

Merged best-of-both structure (calm hero, money proof, the software+service model, the named charges):

1. **Hero** — calm-confidence headline *"Know your fuel bill is right"* + money subhead (*"...stop paying for fuel you never got"*) with the proof stat (#4) nearby. CTAs: *"Talk to us about FuelMatch"* / *"See how FuelMatch works."*
2. **The problem** — a load lives in four places (the truck, the paper BOL at the store, the Vendor Portal invoice, the bank draft); nobody matches them by hand; **the auto-draft can pay before anyone checks** (the ticking clock). Callout: the $39,600 phantom example.
3. **What FuelMatch does — software + service** (3 beats): (a) your store scans the BOL; (b) FuelMatch checks the invoice gallons against the BOL; (c) **Trasio works the dispute with the vendor — not you.**
4. **The proof (made concrete)** — lead with **"8,800 gallons invoiced, no BOL on file → $39,600 you should not pay."** Back it with the over-billing case *"Vendor billed 142 gallons more than the truck dropped."* Show the number, not an adjective.
5. **The charges FuelMatch catches** — two public cards: **Phantom Delivery** ($39,600 *example*) · **Volume Overbilling** ($3,600 on 800 gal). *(Price Variance is coded but hidden — keep it off the page until it ships, then it becomes a third card.)*
6. **Software that watches, service that works** — two columns. Left (software): BOL scanner, automatic reading, BOL↔invoice matching, the reconciliation dashboard, SMS/in-app alerts. Right (service): human exception review, runs the vendor calls/emails for you, verifies the charge is reversed. One-liner: *"automation without a back-office reconciliation team."*
7. **What changes for an owner-operator** — Fewer surprises · Less hassle (your team scans; Trasio chases) · Protected margin (one caught load pays for it).
8. **Inside FuelMatch** — dashboard screenshots: exception-first reconciliation view (ranked "needs attention" cards), the green-headed Fuel Purchases report, an SMS-alert mockup.
9. **Platform fit** — runs alongside ShiftClose on the same tablets + login; ShiftClose protects cash/inventory at handoff, FuelMatch protects fuel spend.
10. **Objections** — "New hardware?" No. "Works with my supplier?" Yes — scan the paper BOL, forward (or key) the invoice. "How long to set up?" Minutes — it rides on the tablet you already use.
11. **CTA** — *"Schedule a FuelMatch walkthrough"* (consultative, fits the service) + the audit hook *"Send last month's deliveries — we'll show you what you overpaid."* Add-on for existing Trasio stores; standalone for multi-site owner-operators.

---

## 4. Cross-cutting

- **Killer GTM mechanic — a free "Fuel Audit" lead magnet.** Operator sends last month's BOLs + invoices; we run the reconciliation and return *"here's the $X you overpaid."* Executable **today** with the manual pipeline, turns an abstract claim into a personalized number, and beats "watch a demo." Build the fuel page around this offer.
- **Pricing — "Contact us" for now (decided 2026-06-15).** No published FuelMatch price; the consultative CTA carries it. Fits the managed-service model — price on value (a fraction of what we recover) in the sales conversation, not a flat published tier. Revisit a public price once a few audits set the ROI baseline.
- **Brand/visual assets to produce:** dashboard screenshots (green tables, exception cards), an SMS-alert mockup, and reuse the **canonical verification artifact** with `RECONCILED` / `VARIANCE DETECTED · UNRESOLVED` state words so the page is unmistakably Trasio.
- **SEO:** new keyword cluster — *fuel delivery reconciliation, bill of lading reconciliation, fuel overbilling, c-store fuel margin, BOL audit.* Net-new surface area ShiftClose owns none of.

---

## 5. ⚠️ Pre-mortem — claims must match what's deployable

The 30-second flaw a sharp visitor would catch: **selling capabilities that aren't built.** Keep the page honest to founding-store reality:

- **Alerting claim — KEPT (decision 2026-06-15).** "Discrepancy alerts to your phone" stays as a benefit. It is not built yet (workstream K.32, blocked), so this is now a **commitment**: build alerting for the first founding cohort so the promise holds when they sign.
- **Bank claim — OFF the page (decision 2026-06-15).** Public claim is two-way **BOL ↔ invoice**, which is deployable today and is exactly what the $39,600 "invoiced, no BOL" finding proves. Three-way bank/EFT reconciliation stays internal roadmap until Plaid is wired (invoice-# limitation).
- **The $39,600 figure is REPRESENTATIVE, not a real recovery (confirmed 2026-06-15).** So label it on the page as an **example/illustration** ("e.g., 8,800 gal invoiced with no BOL = $39,600") — never as "we recovered $X for a store." The audit lead magnet supplies the operator's real number; that's where a true recovery stat comes from later.
- **The "we work the vendor dispute for you" service is founder-led concierge today**, not a staffed back-office. Do-things-that-don't-scale is right for the founding cohort — but stage the language so it doesn't imply a team that doesn't exist.
- **Price Variance = coded but hidden (decision 2026-06-15).** Build the contract-rack-price check behind a flag, but keep it OFF all public copy — page cards, home card, SEO meta, OG — until it ships. Public surface = two charges (Phantom Delivery + Volume Overbilling). Re-add Price Variance copy + the "price errors" keyword when it goes live.
- **"Checks invoices in the background / pulls the Vendor Portal invoice" oversells automation** — invoice intake is manual entry or email-forward today (a Vendor Portal pull is roadmap). Soften "background/automatic" to match.

---

## 6. Open decisions / inputs needed

**Resolved 2026-06-15:** name = **Trasio FuelMatch** · canonical URL = **/fuelmatch** · headline proof = **"8,800 gal invoiced, no BOL → $39,600" (representative example)** · alerting claim **kept** (build commitment) · bank/three-way claim **deferred** · Price Variance **coded but hidden** (off public copy) · pricing = **"Contact us"** (value-priced managed service).

Still open:
- **Build approach for the static site** (`index.html` is a single hand-built HTML file ~53KB; per-product pages = new `shiftclose.html` / `fuelmatch.html` or a templating step — decide before implementation).

---

## 7. SEO / social metadata — `/fuelmatch` (ready)

From the designer, with "price errors" / contract-price removed (Price Variance is hidden — re-add when it ships):

- **Page title (~64 chars):** `Trasio FuelMatch — Fuel Invoice Reconciliation for Convenience Stores`
- **Meta description (~125 chars):** `Trasio FuelMatch checks BOLs against vendor invoices and catches phantom deliveries and overbilling. Keep every dollar you're owed.`
- **H1:** `Know your fuel bill is right.` (matches the hero; differs from the title to avoid duplicate-signal)
- **Open Graph:** `og:title` = `Trasio FuelMatch — Stop Overpaying for Fuel` · `og:description` = `Trasio catches phantom deliveries and overbilling on every fuel load — and works the dispute with the vendor so you don't have to.` · `og:image` = FuelMatch dashboard screenshot / branded card · `og:url` = `https://www.trasio.app/fuelmatch` · `og:type` = `website`

Paste-ready `<head>` block:

```html
<title>Trasio FuelMatch — Fuel Invoice Reconciliation for Convenience Stores</title>
<meta name="description" content="Trasio FuelMatch checks BOLs against vendor invoices and catches phantom deliveries and overbilling. Keep every dollar you're owed." />
<meta property="og:title" content="Trasio FuelMatch — Stop Overpaying for Fuel" />
<meta property="og:description" content="Trasio catches phantom deliveries and overbilling on every fuel load — and works the dispute with the vendor so you don't have to." />
<meta property="og:url" content="https://www.trasio.app/fuelmatch" />
<meta property="og:type" content="website" />
```

*Diff vs. the designer's draft: dropped "and price errors" (meta + OG) and "contract rack price" (home Card 2) to keep public copy consistent with Price Variance being coded-but-hidden. Also add a `<link rel="canonical" href="https://www.trasio.app/fuelmatch" />` and reuse the existing `og:image` dimensions from `index.html`.*

---

## Suggested first slice (ship fast)

Nav dropdown + home two-product split + a single `/fuel` page built around the **free Fuel Audit** offer, with honest founding-store claims. Pricing and full content parity follow.
