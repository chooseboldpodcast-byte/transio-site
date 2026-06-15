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

## 2. Site structure changes

- **Nav:** `Product` → **`Products ▾`** dropdown (ShiftClose · FuelMatch). Keep `Technology · Pricing · Blog`. CTA stays "Join Founding Stores."
- **Home hero:** unchanged headline; add a one-line product subhead or thin band under it: *"Two products on one perception layer — close shifts in 5 minutes, and catch every fuel delivery you overpaid."*
- **New "Two products" split section** (after hero, before deep content): two cards — ShiftClose (saves time) / FuelMatch (recovers money) — each linking to its page.
- **`/shiftclose`** — existing deep content (Sarah/Mike scenarios, three benefits, Inside ShiftClose) moves here largely as-is.
- **`/fuel`** — new page (section outline in §3).
- **Pricing page** — add fuel tier / bundle (§4).
- **Footer** — add Products links.

---

## 3. The `/fuel` product page — section by section

Mirror the ShiftClose page *rhythm* (same family) but lead with money:

1. **Hero** — money headline + perception as mechanism + CTA *"See what you overpaid last month"* (the audit lead magnet, §4). Pair the headline with the proof stat from #4.
2. **The problem** — nobody checks that the gallons *delivered* (the BOL the driver hands you) match the gallons *billed* (the supplier invoice). It's manual, so it doesn't happen — and you pay for fuel that never came off the truck.
3. **How it works** — three steps, the *Perceive → Reconcile → Flag* motion: scan the BOL (camera / Claude vision) → reconcile it against the supplier invoice (BOL ↔ invoice, by grade and total) → flag the variance.
4. **The proof (made concrete)** — lead with the headline finding: **"8,800 gallons invoiced, no BOL on file → $39,600 you should not pay."** Back it with the over-billing case: *"BP billed 142 gallons more than the truck dropped."* Show the number, not an adjective — it's the single most persuasive asset on the page.
5. **Three benefit callouts** (parallel to ShiftClose's time/audit/accuracy): **Money recovered** · **Every delivery verified** · **Discrepancy alerts to your phone**.
6. **Inside FuelMatch** — dashboard screenshots: exception-first reconciliation view (ranked "needs attention" cards), the green-headed Fuel Purchases report, an SMS-alert mockup.
7. **Why it works / why now** — camera-first (no supplier API needed; manual or emailed invoice today), runs on the tablet you own, catches the discrepancy before you cut the check.
8. **Objections** — "New hardware?" No. "Works with my supplier?" Yes — scan the paper BOL, forward (or key) the invoice. "How long to set up?" Minutes — it rides on the tablet you already use.
9. **CTA** — *"Send us last month's deliveries — we'll show you what you overpaid"* + Join Founding Stores.

---

## 4. Cross-cutting

- **Killer GTM mechanic — a free "Fuel Audit" lead magnet.** Operator sends last month's BOLs + invoices; we run the reconciliation and return *"here's the $X you overpaid."* Executable **today** with the manual pipeline, turns an abstract claim into a personalized number, and beats "watch a demo." Build the fuel page around this offer.
- **Pricing:** standalone tier vs. bundle vs. upsell to ShiftClose stores. Money-recovery products price on value, but a flat add-on tier is cleaner for founding stores. Needs a real $ figure + your call.
- **Brand/visual assets to produce:** dashboard screenshots (green tables, exception cards), an SMS-alert mockup, and reuse the **canonical verification artifact** with `RECONCILED` / `VARIANCE DETECTED · UNRESOLVED` state words so the page is unmistakably Trasio.
- **SEO:** new keyword cluster — *fuel delivery reconciliation, bill of lading reconciliation, fuel overbilling, c-store fuel margin, BOL audit.* Net-new surface area ShiftClose owns none of.

---

## 5. ⚠️ Pre-mortem — claims must match what's deployable

The 30-second flaw a sharp visitor would catch: **selling capabilities that aren't built.** Keep the page honest to founding-store reality:

- **Alerting claim — KEPT (decision 2026-06-15).** "Discrepancy alerts to your phone" stays as a benefit. It is not built yet (workstream K.32, blocked), so this is now a **commitment**: build alerting for the first founding cohort so the promise holds when they sign.
- **Bank claim — OFF the page (decision 2026-06-15).** Public claim is two-way **BOL ↔ invoice**, which is deployable today and is exactly what the $39,600 "invoiced, no BOL" finding proves. Three-way bank/EFT reconciliation stays internal roadmap until Plaid is wired (invoice-# limitation).
- **The $39,600 headline figure** should be grounded in a real or representative audit before it leads the page — a fabricated ROI stat is the one thing that breaks trust on a money product. The audit lead magnet backstops this: it proves value with the operator's own data instead of a stated stat.

---

## 6. Open decisions / inputs needed

**Resolved 2026-06-15:** name = **Trasio FuelMatch** · headline proof = **"8,800 gal invoiced, no BOL → $39,600"** · alerting claim **kept** (now a build commitment) · bank/three-way claim **deferred off the public page**.

Still open:
- **Standalone vs. bundle pricing** intent (and a real $ figure beyond the headline example).
- **Build approach for the static site** (`index.html` is a single hand-built HTML file ~53KB; per-product pages = new `shiftclose.html` / `fuel.html` or a templating step — decide before implementation).

---

## Suggested first slice (ship fast)

Nav dropdown + home two-product split + a single `/fuel` page built around the **free Fuel Audit** offer, with honest founding-store claims. Pricing and full content parity follow.
