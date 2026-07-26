# Case: hoodlings.xyz

Site: https://www.hoodlings.xyz/ — "HoodLings HQ whitelist application on Robinhood Chain".

Structure (React SPA, assets index-*.js):
- Landing: logo, "Meet the HoodLings", heading "Join the HoodLings Clan", button
  "APPLY FOR WHITELIST", footer X link.
- Click "APPLY FOR WHITELIST" → modal "APPLICATION IN PROGRESS", STEP 1 OF 5.
- Step 1: "Follow HoodLings" → link "Follow @hoodlingsHQ Open Twitter" + textbox "username"
  + CONTINUE (disabled until follow verified).

Steps 2–5 were not reached (verification gated). Based on typical patterns: likely
retweet / join Discord / submit Robinhood wallet address / maybe signature.

Resolution in session: typed `@0xmaduro` into username box, but CONTINUE stayed disabled
because follow must be verified server-side via X API (agent has no X token). Escalated to
user: "follow @hoodlingsHQ manually, then supply X API token if you want automation."

Lesson: whitelist "follow" steps are NOT click-only. They need X connect/verify → fall under
the escalate rule, not the click-only rule.
