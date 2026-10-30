# North Cedar Software — app showcase site (northcedarsoftware.com)

Static site, no build step. Structure:

- `index.html` → studio home with the apps grid (add one `.app-card` per new app)
- `apps/invoicepop/index.html` → InvoicePop presentation page
- `style.css`, `favicon.svg`, `assets/invoicepop-icon.png` (the real app icon, taken from the project assets)
- `CNAME` → apex domain for GitHub Pages

Adding an app later: copy `apps/invoicepop/` as the template for `apps/<newapp>/`, swap icon/text, add a card on the home grid, and give the new app its own support subdomain + privacy/delete pages (same pattern as InvoicePop).

## Deploy on GitHub Pages (apex domain)

1. Create a **public** repo (e.g. `northcedar-site`) and upload these files at the root.
2. Repo → Settings → Pages → Source: **Deploy from a branch**, `main` / `(root)`.
3. In **Namecheap** → Domain List → northcedarsoftware.com → Manage → **Advanced DNS**, add:
   - 4 × **A Record**, Host `@`, Values: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - 1 × **CNAME Record**, Host `www`, Value `<your-github-username>.github.io`
   - ⚠️ Do NOT touch the MX records — they belong to the support@ mailbox (Namecheap Private Email).
4. Back in GitHub Pages settings, the custom domain should read `northcedarsoftware.com` (from the CNAME file). After the DNS check passes and the certificate is issued, tick **Enforce HTTPS**.
5. The InvoicePop support pages are a SEPARATE repo/subdomain (see the `invoicepop-support-site` package): CNAME host `invoicepop` → `<your-github-username>.github.io`. This showcase site links to those pages.

## Before launch checklist

- [x] Real screenshots are in (`assets/shots/` — Documents, Materials & Services, Settings, taken on Android; the Settings shot is privacy-safe — it shows “Current business”, not real business names). Note: the Documents shot is an empty state (all balances CAD 0.00) — swap in richer shots with sample/live data any time by replacing the files with the same names.
- [ ] When InvoicePop is live on Google Play: on `apps/invoicepop/index.html`, find the `PLAY LINK` comment — remove class `disabled`, set the real Play URL, and change the label to “Get it on Google Play”.
- [ ] Everything the FAQ says is true of the app today (no payment processing, guest mode, voice/AI consent, email account deletion). Re-check the copy whenever the app’s features change.
