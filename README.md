# retirementcalc
# Savings Need Estimator

A single-page web app that projects how a 529 (or any investment account) grows over
time and how much it can pay out. Edit the assumptions on the left; every projection,
chart, and table updates live. It faithfully reproduces the math from the original
spreadsheet — verified to the dollar against the sample tables.

There is **no build step and no dependencies**. It's one `index.html` file, so it runs
anywhere, including free GitHub Pages hosting.

---

## What it does

- **Balance projection** — starting savings plus a yearly contribution that can stay
  level or step up each year, compounded at your rate of return.
- **Plan two ways** — enter an annual contribution and see the result, *or* enter a
  target balance and let it solve for the contribution you need.
- **Future vs. today's dollars** — toggle to discount by inflation so you see what the
  money will actually feel like.
- **Payout estimate** — spreads the goal-year balance across your payout years (e.g. 4
  years of college), after tax.
- **Sensitivity tables** — sweeps five contribution levels across the years, with the
  cell matching *your* plan at *your* goal year highlighted.

### The core formula (verified against the spreadsheet)

```
balance at year n = assets·(1+return)^n
                  + Σ (k=1..n)  contribution·(1+increase)^(k-1)·(1+return)^(n-k)
```

---

## Deploy it on GitHub Pages (no command line needed)

1. Sign in at [github.com](https://github.com) and click **New repository**.
2. Name it something like `savings-estimator`, keep it **Public**, click **Create**.
3. On the new repo page click **uploading an existing file**, then drag in
   `index.html` (and this `README.md`). Click **Commit changes**.
4. Go to **Settings → Pages**.
5. Under **Build and deployment**, set **Source = Deploy from a branch**, pick branch
   `main` and folder `/ (root)`, then **Save**.
6. Wait ~1 minute. Your app is live at
   `https://YOUR-USERNAME.github.io/savings-estimator/`.

To change anything later, edit `index.html` in GitHub (pencil icon) and commit — the
site updates automatically.

## Or with the command line

```bash
git init
git add index.html README.md
git commit -m "Savings Need Estimator"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/savings-estimator.git
git push -u origin main
# then enable Pages in Settings → Pages as above
```

## Run it locally

Just double-click `index.html`. That's it.

---

## Customize

Everything lives in `index.html`:

- **Default numbers** — search for the `DEFAULTS` object in the script and change them.
- **Colors** — edit the CSS variables in the `:root { ... }` block at the top.
- **Number of table columns** — the tables show five levels; change the loop in
  `columnLevels`.

## Notes

This is a planning estimate, not financial advice. Real returns, taxes, contribution
limits, and fees vary. Qualified 529 withdrawals for education are generally federal-tax-free,
which is why the tax rate defaults to 0%.
