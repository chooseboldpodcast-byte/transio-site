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
- **(B) Platform home + per-product pages** *(recommended)* — `/shiftclose` and `/fuel`. Current deep ShiftClose content moves to `/shiftclose`; home keeps hero + a two-product split + top proof.
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

1. **FuelMatch is software + SERVICE, not just a detector — the biggest upgrade.** Trasio doesn't only flag a bad load; **Trasio works the dispute with BP on the operator's behalf** (makes the calls/emails, verifies the charge is reversed or never collected). For time-poor owner-operators this is a far stronger value prop and a real moat — *"automation without building a back-office reconciliation team."* Reframe the product as a **managed service with software underneath** (this also unlocks value-based pricing vs. a flat tool fee).
2. **Name the three charges in operator language** (use these on the public page instead of the engine's status names):
   - **Phantom Delivery Charge** — invoiced for a load with no BOL on file *(= `missing_bol`)*. Hero example: 8,800 gal × $4.50 = **$39,600**.
   - **Volume Overbilling** — invoice gallons > BOL gallons *(= `gallons_mismatch`, BP > BOL)*. Example: BOL 8,000 vs invoice 8,800 → 800 × $4.50 = $3,600.
   - **Price Variance** — invoice $/gal > your contract rack price *(NEW dimension — not built yet; see §5)*.
3. **Use the bank as the ticking clock, not a feature.** *"The bank auto-draft can pay the invoice before anyone checks"* creates urgency (*catch it before the draft clears*) without claiming bank reconciliation — fully compatible with the no-bank-claim decision, and it sharpens it.

Also adopt: a **calm-confidence hero** — *"Know your fuel bill is right"* — paired with the loss proof beneath it (more on-brand than a pure loss-aversion headline); an explicit **ShiftClose platform-fit** section; and **consultative CTAs** ("Talk to us about FuelMatch" / "Schedule a walkthrough").

**Keep from this outline (the draft omits it): the free Fuel Audit lead magnet** — *"send last month's deliveries, we'll show what you overpaid."* It's the strongest top-of-funnel hook **and** it's literally the managed service's first concierge touch. Make it the secondary CTA or a standalone band.

*(Honesty flags on these adopted claims live in §5.)*

---

## 2. Site structure changes

- **Nav:** `Product` → **`Products ▾`** dropdown (ShiftClose · FuelMatch). Keep `Technology · Pricing · Blog`. CTA stays "Join Founding Stores."
- **Home hero:** unchanged headline; add a one-line product subhead or thin band under it: *"Two products on one perception layer — close shifts in 5 minutes, and catch every fuel delivery you overpaid."*
- **New "Two products" split section** (after hero, before deep content): two cards — ShiftClose (saves time) / FuelMatch (recovers money) — each linking to its page.
- **`/shiftclose`** — existing deep content (Sarah/Mike scenarios, three benefits, Inside ShiftClose) moves here largely as-is.
- **`/fuel`** — new page (section outline in §3).
- **Pricing page** — FuelMatch shows **"Contact us"** for now (no published price), consistent with the consultative CTA; ShiftClose pricing unchanged.
- **Footer** — add Products links.

---

## 3. The `/fuel` product page — section by section

Mirror the ShiftClose page *rhythm* (same family) but lead with money:

Merged best-of-both structure (calm hero, money proof, the software+service model, the named charges):

1. **Hero** — calm-confidence headline *"Know your fuel bill is right"* + money subhead (*"...stop paying for fuel you never got"*) with the proof stat (#4) nearby. CTAs: *"Talk to us about FuelMatch"* / *"See how FuelMatch works."*
2. **The problem** — a load lives in four places (the truck, the paper BOL at the store, the BP Portal invoice, the bank draft); nobody matches them by hand; **the auto-draft can pay before anyone checks** (the ticking clock). Callout: the $39,600 phantom example.
3. **What FuelMatch does — software + service** (3 beats): (a) your store scans the BOL; (b) FuelMatch checks the invoice gallons + price against the BOL; (c) **Trasio works the dispute with BP — not you.**
4. **The proof (made concrete)** — lead with **"8,800 gallons invoiced, no BOL on file → $39,600 you should not pay."** Back it with the over-billing case *"BP billed 142 gallons more than the truck dropped."* Show the number, not an adjective.
5. **The three charges FuelMatch catches** — cards: **Phantom Delivery** ($39,600) · **Volume Overbilling** ($3,600 on 800 gal) · **Price Variance** (cents/gal that compound) *(Price Variance = roadmap, §5)*.
6. **Software that watches, service that works** — two columns. Left (software): BOL scanner, automatic reading, BOL↔invoice matching, the reconciliation dashboard, SMS/in-app alerts. Right (service): human exception review, runs the BP calls/emails for you, verifies the charge is reversed. One-liner: *"automation without a back-office reconciliation team."*
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
- **The $39,600 headline figure** should be grounded in a real or representative audit before it leads the page — a fabricated ROI stat is the one thing that breaks trust on a money product. The audit lead magnet backstops this: it proves value with the operator's own data instead of a stated stat.
- **The "we work the BP dispute for you" service is founder-led concierge today**, not a staffed back-office. Do-things-that-don't-scale is right for the founding cohort — but stage the language so it doesn't imply a team that doesn't exist.
- **Price Variance isn't built.** The engine reconciles BOL↔invoice gallons today; it does not yet ingest the operator's contract rack price to compare. Present Price Variance as the third charge "coming," or wire contract-price ingestion before claiming it. (Phantom + Volume Overbilling are real now.)
- **"Checks invoices in the background / pulls the BP Portal invoice" oversells automation** — invoice intake is manual entry or email-forward today (a BP Portal pull is roadmap). Soften "background/automatic" to match.

---

## 6. Open decisions / inputs needed

**Resolved 2026-06-15:** name = **Trasio FuelMatch** · headline proof = **"8,800 gal invoiced, no BOL → $39,600"** · alerting claim **kept** (build commitment) · bank/three-way claim **deferred** · pricing = **"Contact us"** for now (value-priced managed service).

Still open:
- **Build approach for the static site** (`index.html` is a single hand-built HTML file ~53KB; per-product pages = new `shiftclose.html` / `fuel.html` or a templating step — decide before implementation).

---

## Suggested first slice (ship fast)

Nav dropdown + home two-product split + a single `/fuel` page built around the **free Fuel Audit** offer, with honest founding-store claims. Pricing and full content parity follow.
