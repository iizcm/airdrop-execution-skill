---
name: airdrop-execution
description: Execute crypto airdrop / whitelist / quest tasks from websites on the user's behalf. Click-only tasks are automated with the user's public identity; tasks needing X/Twitter connect, wallet signature, or CAPTCHA are escalated to the user with exact steps.
triggers:
  - user sends an airdrop / whitelist / quest website link ("kerjain ini", "claim ini", "daftar whitelist")
  - user says "gue dapet airdrop, linknya ini"
  - any request to complete on-site crypto task steps
---

# Airdrop / Whitelist Task Execution

The user runs many airdrop/whitelist quests. They send website links and want you to
do the work. Core rule they stated: **"cuma diklik aja" — automate sites that need only
clicks; if it needs X connect or wallet, wait for them to supply API token / do it themselves.**

## User public identity (safe to use; from memory — re-confirm if changed)
- X handle: `@0xmaduro` (profile https://x.com/0xmaduro)
- Wallet: `0xBe241c08C26DCbA155009B2b54bb7DB15A7eA02a`
- Other fields (email / discord / real name) supplied per-project as the form demands.
- NEVER use or store seed/keys. Only the public address + X handle go into forms.

## Workflow
1. Open the link with `browser_navigate`.
2. **Many airdrop sites are React SPAs** — the first snapshot often returns 1 empty node
   (`- generic [ref=e1] clickable`). Do NOT conclude the site is broken. Wait 2–3s,
   re-snapshot; if still empty, reload the URL and wait again. (See Pitfalls.)
3. Classify the task:
   - **CLICK-ONLY** (no X connect, no wallet): do it. Fill public identity fields
     (X handle, wallet address). Click through every step.
   - **NEEDS X CONNECT / FOLLOW-VERIFY / API**: fill whatever doesn't require verification,
     then STOP and tell the user exactly what's blocked. Offer to automate if they paste an
     X API token. Until then, do not claim it's "done."
   - **NEEDS WALLET CONNECT / SIGNATURE**: escalate immediately. Agent must never sign
     transactions or connect a wallet — risk of draining funds. User does this in their own wallet.
   - **CAPTCHA / HUMAN CLICK**: escalate, give the user the exact spot to click.
4. Keep a 1-line log per site (what was done / what's blocked) so the user has a status list.
5. If a form asks for a wallet on **Robinhood Chain (chainId 4663)**: the RPC
   `https://rpc.mainnet.chain.robinhood.com/` is reachable from the VPS, but wallet *signing*
   is still user-side. Only paste the public address; never initiate a sign.

## Pitfalls
- React SPA snapshot returns empty/`element_count: 1` → wait + reload, don't abort.
- Whitelist "Follow @handle" steps usually verify server-side via X API. Typing the username
  alone will NOT pass the check. Escalate for X connect.
- Some "apply" buttons open a modal that needs a render delay before the snapshot updates;
  wait ~2s after clicking before snapshotting.
- Never paste the user's seed/key anywhere. Forms only ever get the public address.
- **CEX / exchange airdrops often look like mining but aren't.** If the signup form includes
  hCaptcha, email verification, or KYC policy links, mass-account automation is not viable.
  Escalate immediately rather than attempting to bypass captcha or farm identities.
- **Telegram mini-app bots rarely expose their web URL** in the public t.me preview.
  The user must open the bot in Telegram, press Play/Launch, and copy the actual mini-app
  URL (or send a screenshot). Without that URL, the agent cannot inspect the API surface.

## References
- `references/hoodlings-case.md` — worked example: hoodlings.xyz 5-step whitelist
  (step 1 = follow @hoodlingsHQ, needs X verify → escalated).
- `references/gxtexchange-case.md` — CEX airdrop with hCaptcha + unknown mini-app;
  skipped after inspection showed mass automation was infeasible.
