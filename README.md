# Japan My Number Card Expiry Check

Free checker for when a Japan My Number Card (マイナンバーカード) expires and what to do before then: foreign residents' cards end with the period of stay and are not extended by a visa renewal (city-hall extension deadline, one-time 2-month extension while a renewal is pending, 10th-birthday cap), the 10th / 5th-birthday rule and renewal window for Japanese, PR and SPR holders, e-certificates, the マイナ保険証 grace and the 特定在留カード.

- Full app and API (Vercel): https://japan-mynumber-card-check.vercel.app
- Checker (GitHub Pages): https://akiba-labs.github.io/japan-mynumber-card-check/

- API: `GET /api/check?holder=mid_long&birthDate=1992-04-10&cardIssueDate=2024-03-01&residenceExpiry=2026-12-15&renewal=pending` (keyless, CORS open), `/api/rules`, `/openapi.json`, `/llms.txt`
- MCP: `japan_my_number_card_expiry_check` on https://free-agent-tools.vercel.app/mcp

Sources: 個人番号カード等に関する命令 art. 26, 27, 29 (e-Gov), Digital Agency, ISA (特定在留カード, residence-card renewal), Mynaportal FAQ 10178, MHLW, Matsudo City. Rules as of 2026-10-29.

**Disclaimer:** educational, not legal advice, not affiliated with the Digital Agency, J-LIS, ISA or any city office. The date on your card counts; confirm with your city office.

```
npm install
npm test
npm run build
npm run build:pages
```

`npm run build` is the Vercel app (checker, JSON API, share pages). `npm run build:pages` writes a static `out/` for GitHub Pages and checks that internal links and assets resolve under `/japan-mynumber-card-check`. Server routes stay in the repo; the Pages script only moves them aside for that build.

GitHub settings: **Settings → Pages → Build and deployment → Source: GitHub Actions**. Pushes to `main` deploy with `.github/workflows/pages.yml`. The copy-paste steps for the other tool repos are at the top of `scripts/build-pages.mjs`.
