# BigHammer Informatica Exit webinar (3 December 2026)

Replica of the October masterclass landing page and thank-you page (UK repo `bighammer-masterclass-uk`), rewritten for the Informatica migration webinar.
Files: `index.html`, `thank-you.html`, `og-image.png`, `wrangler.jsonc`, `.assetsignore`.

## Session
Thursday 3 December 2026, 11:00 AM ET (16:00 UTC, 4:00 PM UK, 5:00 PM Central Europe, 8:00 PM Dubai, 9:30 PM India). 60 minutes: 40 demo + 20 live Q&A. Fallback date: Wednesday 2 December, same time. Start timestamp `2026-12-03T16:00:00Z`.

## Needed before going live
1. `BROADCAST_ID` in `index.html` is empty on purpose. Paste the new WebinarGeek broadcast ID (digits only). While it is empty, or equals an October ID (6841508, 6942090), live sign-ups are blocked. There is no "upcoming broadcast" lookup.
2. `LIVE_HOSTS` is `informatica.webinar.bighammerai.com` (proposed). Change it, the og/canonical/JSON-LD URLs and the Cloudflare custom domain together if another hostname is chosen. On any other host sign-ups are simulated.
3. Automations Worker (`workers/automations` in the UK repo): this session is in New York time, which is the Worker's default `WEBINAR_TIMEZONE`, so no `BROADCAST_SESSIONS` entry is needed. Confirm after the first test sign-up that `readable_webinar_date`, `readable_webinar_time` and `webinar_broadcast_date` in GHL are right (Thursday 3 December 2026, 11:00 AM ET, 2026-12-04 02:30:00 IST).
4. GA4, LinkedIn Insight Tag and Metricool IDs are empty in both files (inert until set and the visitor accepts the cookie banner).
5. No WhatsApp on this webinar: the thank-you page has three steps (join link and calendar, book a demo, email confirmation) and the form copy mentions email only. The phone field is still collected and required; make it optional or remove it if the team does not need it.
6. Offer on the page is the 4-week proof sprint on 10-15 workloads (the flyer says 3 to 5; changed per the team). The earlier plan also mentioned a free Informatica Migration Assessment; it is NOT on the page because it is not confirmed.
7. UTM: default `utm_campaign` is `web5-infa-03dec`.

## Messaging requirement
Page copy says BigHammer migrates jobs and workloads from Informatica PowerCenter, Axon, Data Quality and IDMC to any public cloud. The brief said "IDMS"; this assumes Informatica IDMC (Intelligent Data Management Cloud). Change the hero lead, meta description, og description and JSON-LD if that is wrong.

## Source of content
Hero, problem, four stages and proof pack come from "Informatica Flyer_2452.pdf" and bighammer.ai/ai-agent-migrate. No customer quotes or numbers were invented; the one testimonial and the host bios are carried over from the October page.

## How to change the page (edit locally, push, Cloudflare deploys)
1. Edit `index.html` or `thank-you.html` in this folder (`C:\Users\iamal\Claude Code\GC TASK\bighammer-webinar-informatica`).
2. Look at it locally: `py -m http.server 8000` in this folder, then open http://localhost:8000 (sign-ups are simulated there).
3. Commit and push to `main`: `git add -A && git commit -m "what changed" && git push`.
4. Cloudflare Workers Builds (project `bighammer-webinar-informatica`, deploy command `npx wrangler deploy`) picks up the push and publishes to https://informatica.webinar.bighammerai.com/ in about a minute.
5. Check the build under Cloudflare, Workers & Pages, the project, Deployments. If a push does not create a build, the Cloudflare to GitHub link is broken: Settings, Builds, Manage, and reconnect.

Only `index.html`, `thank-you.html` and `og-image.png` are served; everything else is excluded by `.assetsignore`.
