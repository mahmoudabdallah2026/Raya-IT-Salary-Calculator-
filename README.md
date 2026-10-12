# Raya IT · Salary Calculator

A browser-based gross ⇄ net salary calculator built on the **current Egyptian Labor & Tax Law (2026)**. Single self-contained `index.html` — no build step, no dependencies — ready to publish on GitHub Pages.

![Raya IT](assets/logo.png)

## What it does

- **Gross → Net** — take-home pay from any gross package.
- **Net → Gross (gross-up)** — the package needed to deliver a target net (solves for the total net you promise, including fixed monthly allowances).
- **Egyptian statutory calculation** — progressive income tax + social insurance per the figures in force from 1 January 2026.
- **Variable elements** — add SIPS, allowances, incentives, annual bonuses and profit share, each flagged *taxable* / *insurable* independently.
- **Total annual cash** — base + variable + additions, shown gross → net, plus fully-loaded employer cost.

## Calculation basis (2026)

| Item | Value |
|---|---|
| Income-tax brackets | 7 progressive: 0% ≤ EGP 40,000 · 10% · 15% · 20% · 22.5% · 25% · 27.5% > EGP 1,200,000 |
| Personal exemption | EGP 20,000 / year |
| High-earner "bracket melting" | Lower brackets withdrawn as annual taxable income passes 600k / 700k / 800k / 900k; above 1,200,000 only 25% + 27.5% apply (Law 7/2024) |
| Rounding | Annual net taxable income rounded down to the nearest EGP 10 |
| Social insurance — employee | 11% of the insurable wage |
| Social insurance — employer | 18.75% of the insurable wage |
| Director on commercial register | 21% flat on the max insurable wage (self-borne) |
| Insurable wage floor / cap | EGP 2,700 / EGP 16,700 per month |
| Martyrs & Victims Fund | 0.05% of gross — on by default (switchable) |
| Optional | Comprehensive health insurance |

Income tax is applied to salary income **after** deducting employee social-insurance contributions and the personal exemption. All rates and thresholds are editable in the **Advanced** panel to model a future indexation or a different payroll convention.

> Planning aid for Raya IT HR — not tax or legal advice. Confirm executive-level and edge-case figures with Finance / a tax advisor. Reviewed against PwC Worldwide Tax Summaries and NOSI announcements (2026).

## Branding

Navy `#1F3864`, light blue `#EEF4FB`; no pink. The official **RAYA Information Technology** logo is embedded in `index.html` (shown on a white chip in the navy header) and also saved at `assets/logo.png`. To swap it for a different mark, replace `assets/logo.png` and update the embedded `data:image/png;base64,…` in the header `<img>`.

## Run locally

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Publish on GitHub Pages

**Option A — command line**

```bash
git init
git add .
git commit -m "Raya IT salary calculator"
git branch -M main
git remote add origin https://github.com/<your-username>/raya-salary-calculator.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main` / `root` → Save.**
Your calculator goes live at `https://<your-username>.github.io/raya-salary-calculator/` within a minute or two.

**Option B — no command line:** create a new repository on github.com, click **Add file → Upload files**, drag in `index.html`, `README.md`, `.nojekyll` and the `assets/` folder, commit, then enable Pages as above.

The `.nojekyll` file ensures GitHub Pages serves the site exactly as-is.
