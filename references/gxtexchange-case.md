# Case: GXT Exchange Airdrop / Mini-App

Date: 2026-07-23
Site: https://gxtexchange.com/auth?ref=8551BCC6
Mini-app bot: https://t.me/GXTExchangeAirdropBot?start=ref_7027656883

## What the site looked like
- Web signup: standard exchange registration form (username, email, password, confirm, invite code).
- Security: **hCaptcha** widget in the form, submit button disabled until captcha solved.
- Login alternatives: Google sign-in.

## Why this was NOT automatable as "click-only"
1. **hCaptcha** — requires human/bypass service per account.
2. **Email verification** — expected after signup (not observed but standard for CEX).
3. **Mass-account farming would need**: unique email per account, unique IP/device fingerprint, and likely KYC before any token claim.
4. The Telegram bot link did not expose the mini-app web URL directly; it requires opening inside Telegram first.

## How to inspect a Telegram mini-app that isn't exposed
1. Open the bot in Telegram mobile/desktop.
2. Press **Start** and then any **Play / Launch** button.
3. On desktop Telegram: right-click the button → **Copy link** to get the `https://t.me/<bot>?startapp=...` or direct `https://<app>.pages.dev/...` URL.
4. On mobile: long-press the button → copy the link if the client supports it.
5. Send that URL to the agent for API inspection.

## Outcome
Task skipped after user agreed. Recommendation: only pursue if mini-app proves to be a pure API call (no captcha, no KYC, no per-account phone/email).
