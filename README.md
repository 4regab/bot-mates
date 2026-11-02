# Grok Bot Marketplace → Kiro Crew mates

One importable Kiro Crew mate per bot on the [Grok Bot Marketplace](https://x.ai/bot/marketplace). 60 mates. The marketplace had 91 bots. 31 that need a tool Kiro Crew has no equivalent for (X, video editing, image generation, hosted cloud coding agents, the Grok CLI and others) were left out. One mate, tinkabot, keeps one gap, marked in bold below, and its rules say how to work around it.

## Import a mate

`crewjam/` holds one `.crewjam` file per mate. In the dashboard: **Mates → Import mate → Choose a file**, pick one, then press **Import mate**. Nothing is created before that press.

Each file is a zip in the same layout Kiro Crew's own "Export as file" writes. Text is copied word for word from the bot's page:

- `crewjam.json`: the bot's name and description.
- `rules.json`: the bot's notes (its memories), then its routines and integrations, then the source link. Rules hold at most 4,000 characters. When a bot's notes are longer, the rest goes in a `<bot>-more` skill and the rules say to read it (9 bots).
- `skills/<name>/SKILL.md`: one skill per playbook on the bot's page.
- `agent.json`: empty.

Routines are listed as text, not schedules: the pages give no times. Skills stay off until you trust the mate's workspace folder. To change a mate, import it and edit it in its profile.

What an import does not carry: MCP servers (this Kiro Crew version refuses them in an import). Connect the tools listed under "Missing tools" below after importing.

## Connect the missing tools with Composio

[Composio](https://composio.dev/toolkits) covers most of the tools these mates need through one MCP server or one CLI, and it handles the logins (OAuth) for you. This saves adding a separate server per app. You need a Composio account.

- **MCP:** add Composio's MCP server in **Connections** as a remote server (`{ "url": "<your Composio MCP URL>" }`), then connect each app in Composio.
- **CLI:** install the Composio CLI. A mate can then call it through the shell.

Composio has a toolkit page for: Slack, Gmail, Outlook, Google Sheets, Google Calendar, Google Drive, Google Slides, OneDrive, Granola, Salesforce, HubSpot, Attio, Gong, Hex, Databricks, Datadog, Ashby, Ramp, NetSuite, Google Ads, Meta Ads and Google Search Console.

No Composio toolkit was found for Apple Search Ads, Plaid or Zapier. Those still need their own server or a manual step. Composio was not tested with these mates.

`tool-map.json` holds the shared tool table and status legend.

## Tool status legend

| Status | Meaning |
|---|---|
| `built-in` | Kiro Crew ships it |
| `catalogue` | In Kiro Crew's Connections catalogue (connect in the dashboard; some cards need an operator OAuth app or are hidden, then add the MCP endpoint by hand) |
| `custom-mcp` | No catalogue entry. Works only if you add an MCP server or script yourself. Availability of a vendor MCP server is not verified here |
| `gap` | No comparable Kiro Crew capability. The mate runs without it and says so |

## Mates

"Missing tools" lists `gap` items in bold and `custom MCP` items after them. Tools that are built in or in the Connections catalogue are not listed. Each mate's creator shows as **From** when you import it.

| Mate | Description | Category | Missing tools |
|---|---|---|---|
| [Account Research Desk](crewjam/account-book.crewjam) | Researches the companies you sell to and writes your pre-call brief and account plan. | From Grok Bot Team, Sales | custom MCP: Gmail, Google Calendar, Google Drive, Google Sheets, Granola meeting notes, Salesforce CRM, Slack workspace read/post |
| [GTM Account Research](crewjam/account-research.crewjam) | Researches one account before a meeting, deal review, or account plan. | From Grok Bot Team, Sales | custom MCP: Gmail, Google Calendar, Google Sheets, Granola meeting notes, Salesforce CRM, Slack workspace read/post |
| [AI Search Visibility](crewjam/ai-search-visibility.crewjam) | Checks whether AI assistants and Google recommend you, and who they name instead. | From Grok Bot Team, Marketing | custom MCP: Google Sheets, Hex analytics notebooks, Profound AI-search visibility, Slack workspace read/post |
| [Alfred](crewjam/alfred.crewjam) | Designs, audits, and governs your Grok Bot organization so it matches real company outcomes, with clear human owners and no duplicate jobs. | Operations | none |
| [Apple Search Ads Review](crewjam/apple-search-ads-review.crewjam) | Reviews your Apple Search Ads spend against your cost per install target. | From Grok Bot Team, Marketing | custom MCP: Ad platform accounts (Apple Search Ads, Google Ads, Meta Ads), Databricks SQL, Gmail, Google Sheets, Hex analytics notebooks, Slack workspace read/post |
| [Call Follow-Ups](crewjam/call-follow-ups.crewjam) | Turns each recorded call into a follow-up email in your voice, a next-steps note, and the CRM updates, including the qualification fields your team runs on. | From Grok Bot Team, Sales | custom MCP: Attio CRM, Gmail, Gong call recordings, Google Calendar, Granola meeting notes, HubSpot CRM, Outlook mail, Salesforce CRM |
| [Chief Health Officer](crewjam/chief-health.crewjam) | You're the Chief Health Officer. | Personal | custom MCP: Workout, nutrition, wearable and lab data |
| [Company Docs Q&A](crewjam/company-docs-q-a.crewjam) | Answers product and how-to questions from live docs first, then connected knowledge sources, and always cites sources. | From Grok Bot Team, Sales | custom MCP: Gmail, Google Calendar, Google Drive, Google Sheets, Slack workspace read/post, Zapier actions |
| [Competitor Watch](crewjam/competitor-watching.crewjam) | Tracks competitor pricing, product, and hiring pages and briefs you on real changes. | Product | custom MCP: Slack workspace read/post |
| [Cooper](crewjam/cooper.crewjam) | News agent for AI, tech, venture capital, and business. | From Grok Bot Team, Sales | custom MCP: Slack workspace read/post |
| [Credit Card Max](crewjam/credit-card-max.crewjam) | Credit card maxing with live Grok Finance (Plaid): which card to swipe given your priorities (points, cash back, airline/hotel status), statement-credit tracking with muteable expiry nags, wrong-card recurring flags, and a monthly points-and-perks rollup — not budgeting. | Personal | custom MCP: Plaid-linked card and transaction data |
| [Critiquito: Design Critique](crewjam/critiquito.crewjam) | Turns a screenshot or Figma link into a design critique with ranked, concrete fixes. | From Grok Bot Team, Design | custom MCP: Slack workspace read/post |
| [Customer Call Coach & Assistant](crewjam/customer-call-coach.crewjam) | Briefs you before customer calls and coaches you after based on your performance. | From Grok Bot Team, Sales | custom MCP: Gmail, Granola meeting notes, Slack workspace read/post |
| [Product Support Inbox Assistant](crewjam/customer-question-drafter.crewjam) | Helps you find and draft answers to product questions. | From Grok Bot Team, Sales | custom MCP: Gmail, Granola meeting notes, Slack workspace read/post |
| [Customer Proof Desk](crewjam/customer-stories.crewjam) | Turns call notes and transcripts into case studies, testimonials, and proof points. | Sales | custom MCP: Gmail, Granola meeting notes, Hex analytics notebooks, Slack workspace read/post |
| [Partnerships Call Coach](crewjam/dan-lanning.crewjam) | Pitch and delivery coach for partnership, sponsorship, and high-stakes discovery calls. | From Grok Bot Team, Sales | custom MCP: Google Calendar |
| [Deal Hunting](crewjam/deal-hunting.crewjam) | Landed-cost shopping: real prices, shipping and tax, preferred retailers. | Personal | none |
| [Deal Inspector](crewjam/deal-qualification.crewjam) | Checks every deal that moved stage against your qualification criteria using the actual call transcripts. | From Grok Bot Team, Sales | custom MCP: Attio CRM, Gmail, Gong call recordings, Google Sheets, Granola meeting notes, HubSpot CRM, Salesforce CRM, Slack workspace read/post |
| [dial bot](crewjam/dial-bot.crewjam) | Places outbound Bland AI phone calls when you ask, then reports what happened. | From Grok Bot Team, Personal | custom MCP: Bland AI phone calls |
| [EBR & Value Deck Builder](crewjam/ebr-value-deck-builder.crewjam) | Builds an executive business review or value deck for a named account from your CRM, call history, and usage data, on your brand, and hands you an editable file. | From Grok Bot Team, Sales | custom MCP: Attio CRM, Gong call recordings, Google Drive, HubSpot CRM, OneDrive, Salesforce CRM |
| [Meeting Recap Deck](crewjam/echo.crewjam) | Turns your meeting notes into a recap deck in your slide template. | From Grok Bot Team, Sales | custom MCP: Gmail, Gong call recordings, Google Calendar, Google Slides, Granola meeting notes, Slack workspace read/post |
| [Event Producer](crewjam/event-producer.crewjam) | Turns your event details into a run of show, guest list, and day-of checklist. | From Grok Bot Team, Marketing | custom MCP: Gmail, Google Calendar, Google Sheets, Slack workspace read/post |
| [Event Request Desk](crewjam/event-request-desk.crewjam) | Scores every event, sponsorship, and speaking ask, then drafts your yes or no. | From Grok Bot Team, Operations | custom MCP: Gmail, Google Calendar, Google Drive, Google Sheets, Hex analytics notebooks, Slack workspace read/post |
| [figma bro](crewjam/figma-bro.crewjam) | Turns a Figma frame into a build spec, and audits your components, tokens, and motion. | From Grok Bot Team, Design | custom MCP: Slack workspace read/post |
| [GTM Loop Closer](crewjam/follow-through-agent.crewjam) | Finds promises, follow-ups, and customer details left behind in meetings, email, Slack, CRM, or task tools. | From Grok Bot Team, Sales | custom MCP: Gmail, Google Calendar, Google Sheets, Granola meeting notes, HubSpot CRM, Salesforce CRM, Slack workspace read/post |
| [Executive Assistant](crewjam/frank.crewjam) | EA chief-of-staff bot for exec support: conference rooms, interview prep, leadership outreach, Slack channel inventories, sheet↔calendar checks, and birthday/anniversary calendar loads. | From Grok Bot Team, Operations | custom MCP: Gmail, Google Calendar, Google Sheets, Slack workspace read/post |
| [Ad Spend Watch](crewjam/fuse.crewjam) | Watches your ad spend and performance and flags what's breaking before it burns budget. | From Grok Bot Team, Marketing | custom MCP: Ad platform accounts (Apple Search Ads, Google Ads, Meta Ads), Datadog, Gmail, Google Sheets, Hex analytics notebooks, Slack workspace read/post |
| [Haggle Bot](crewjam/haggle-bot.crewjam) | Inventories your SaaS spend from Ramp and bills, finds evidence-backed savings (unused seats, duplicates, cheaper alternatives), and drafts vendor counters for your review. | From Grok Bot Team | custom MCP: ERP (for example NetSuite), Gmail, Google Drive, Google Sheets, Granola meeting notes, Ramp spend data, Slack workspace read/post |
| [Hiring Signals](crewjam/hiring-activity-monitor.crewjam) | Tracks hiring activity across selected companies and job sources. | From Grok Bot Team, Sales | custom MCP: Google Sheets, HubSpot CRM, Salesforce CRM, Slack workspace read/post |
| [Home robots](crewjam/home-robots.crewjam) | Control home robots from chat: a Segway Navimow, a Matic vacuum, and other official vacuums, mowers, and Matter robots. | Personal | custom MCP: Home Assistant / Matter / vendor robot SDKs |
| [Copy Humanizer](crewjam/human-copywriter.crewjam) | Edits and rewrites drafts, emails, and pages so they read like a person wrote them. | Marketing | custom MCP: Gmail, Slack workspace read/post |
| [Imogen](crewjam/imogen.crewjam) | Imogen the Impala Image Interpreter writes brief, copyable alt text focused on the most important part of an image, so images are accessible to blind people. | Design | none |
| [Import Bot](crewjam/import-bot.crewjam) | Brings your setup from Claude Cowork, Codex, ChatGPT, OpenClaw, and Hermes into Grok Bot, then creates the expert bots that cover it or adds to the bots you already have. | From Grok Bot Team, Personal | custom MCP: Gmail, Google Drive |
| [Lead Pipeline Desk](crewjam/leadsworth.crewjam) | Scores your inbound leads, merges duplicates, assigns an owner, and flags what's stuck. | From Grok Bot Team, Marketing | custom MCP: Databricks SQL, Gmail, Google Sheets, Hex analytics notebooks, Salesforce CRM, Slack workspace read/post |
| [Love ❤️](crewjam/love.crewjam) | Takes the admin out of being a good Partner so the attention can go where it counts. | Personal | custom MCP: Gmail, Google Calendar |
| [Marketing Analyst](crewjam/marketing-analyst.crewjam) | Google Ads–first performance analyst: turns exports into weekly and monthly reports with commentary, answers reporting asks with real numbers, and watches spend against your thresholds so you catch what’s breaking before it burns budget. | Marketing | custom MCP: Ad platform accounts (Apple Search Ads, Google Ads, Meta Ads), Gmail, Google Drive, Google Sheets, Slack workspace read/post |
| [Project Manager](crewjam/marketing-project-manager.crewjam) | Marketing project manager that coordinates research, positioning, landing pages, ads, and analytics across specialist bots — with screenshot check-ins and human gates on merge and spend. | Marketing | custom MCP: Google Calendar, Google Drive, Slack workspace read/post |
| [Recruiting Coordinator](crewjam/mr-toms.crewjam) | Schedules interview loops, preps your interviewers, and chases what's stalled. | From Grok Bot Team, Recruiting & People | custom MCP: Ashby recruiting ATS, Gmail, Google Calendar, Google Sheets, Granola meeting notes, Slack workspace read/post |
| [NYC Parent](crewjam/nyc-parent.crewjam) | A family chief of staff for New York City parents. | Personal | custom MCP: Gmail, Google Calendar |
| [Office Ops Desk](crewjam/office-ops-desk.crewjam) | Tracks office shipments, facilities issues, and team birthdays, then writes the digests. | From Grok Bot Team, Operations | custom MCP: Gmail, Google Calendar, Google Sheets, Slack workspace read/post |
| [Performance Marketer](crewjam/performance-marketer.crewjam) | A performance marketer that turns Product Marketer ad copy into paused Maximize-clicks Google Ads Search shells for messaging tests — review sheets first, then traffic with live screenshots, no spend until you say so. | Marketing | custom MCP: Ad platform accounts (Apple Search Ads, Google Ads, Meta Ads), Google Drive, Google Sheets, Slack workspace read/post |
| [Pipeline Pulse](crewjam/pipeline-health-and-forecast.crewjam) | Scans your full pipeline for movement, stale next steps, forecast risk, and CRM gaps. | From Grok Bot Team, Sales | custom MCP: Gmail, Google Sheets, Granola meeting notes, HubSpot CRM, Salesforce CRM, Slack workspace read/post |
| [Pitch Deck Coach](crewjam/pitch-deck-coach.crewjam) | Reviews a pitch deck and reports what an investor is likely to understand, believe, question, and remember, then helps strengthen the story, evidence, and slides. | Sales | none |
| [PM bot](crewjam/pm-bot.crewjam) | Acts as your PM. | Product | none |
| [Product Idea Stress Test](crewjam/product-idea-stress-test.crewjam) | Investigates a product or startup idea for founders. | Product | none |
| [Projects Manager](crewjam/projects-manager.crewjam) | Runs your team's projects from Notion: one row per project, a channel per project, and tasks your specialist bots claim. | From Grok Bot Team, Engineering | custom MCP: Slack workspace read/post |
| [QA bot](crewjam/qa-bot.crewjam) | Acts as your QA on the live deploy: runs the acceptance checklist and says pass or fail before you ship. | Engineering | none |
| [SWE](crewjam/seed-a91e4c.crewjam) | Cursor's software engineer bot: writes code, triages issues, monitors production, and more. | Engineering | none |
| [SEO & AEO Desk](crewjam/seo-aeo-desk.crewjam) | Turns your keywords into content ideas and writer-ready briefs for search and AI answers. | From Grok Bot Team, Marketing | custom MCP: Google Search Console, Google Sheets, Profound AI-search visibility, SEO and rank-tracking tools, Slack workspace read/post |
| [Sequencer](crewjam/sequencer.crewjam) | Runs your outbound sequencer as a staff function. | Sales | custom MCP: Gmail, Google Calendar, Google Sheets, Salesforce CRM, Slack workspace read/post |
| [Talent Discovery](crewjam/sherlock.crewjam) | Finds candidates for open roles that match your criteria and aren't already in your ATS. | From Grok Bot Team, Recruiting & People | custom MCP: Ashby recruiting ATS, Gmail, Google Sheets, Slack workspace read/post |
| [Site Audit](crewjam/site-audit.crewjam) | SEO + content + speed + a11y + CRO + schema audit. | Marketing | custom MCP: Lighthouse / PageSpeed Insights, SEO and rank-tracking tools |
| [skippy](crewjam/skippy.crewjam) | A San Francisco street-cleaning assistant. | From Grok Bot Team, Personal | none |
| [Paid Media Report Desk](crewjam/tally.crewjam) | Turns your Google Ads, Meta, and LinkedIn exports into one weekly report with commentary. | From Grok Bot Team, Marketing | custom MCP: Databricks SQL, Gmail, Google Sheets, Hex analytics notebooks, Slack workspace read/post |
| [The Morning Newspaper](crewjam/the-morning-newspaper.crewjam) | A newspaper customized to you. | Personal | custom MCP: Gmail, Google Calendar |
| [tinkabot](crewjam/tinkabot.crewjam) | Wraps an API into a Cursor/Agent Plugin (MCP + skills). | From Grok Bot Team, Engineering | **gap:** Cursor Marketplace / cursor.directory submission; custom MCP: pstack (unclear, named only as an integration on the page) |
| [Tradbot](crewjam/tradbot-2.crewjam) | Watches your personal email and calendar so school forms, bills, and RSVPs don't slip. |  | custom MCP: Gmail, Google Calendar, Slack workspace read/post |
| [Website Ops](crewjam/website-ops.crewjam) | Website operations and content manager. | Marketing | custom MCP: Google Drive, Slack workspace read/post |
| [Writing Bot](crewjam/writing-bot.crewjam) | A writing partner for drafting and revising essays, emails, docs, and other prose. | From Grok Bot Team, Marketing | none |
| [WTD](crewjam/wtd.crewjam) | WTD is a VIP hospitality planning partner for marketing ops — project-plan and status rhythm across tentpoles and ticket banks, nomination-sheet tracking, marketing-visible status hubs, and decks or agendas. | From Grok Bot Team, Marketing | custom MCP: Gmail, Google Drive, Google Sheets, Google Slides, Slack workspace read/post |

## Tool gaps in total

One mate keeps one `gap`: Cursor Marketplace submission (tinkabot, where you submit by hand).

Most common `custom-mcp` needs (you add an MCP server yourself, or use Composio, see above):

- Slack workspace read/post: 37
- Gmail: 31
- Google Sheets: 24
- Google Calendar: 18
- Granola meeting notes: 12
- Google Drive: 11
- Salesforce CRM: 10
- Hex analytics notebooks: 7
- HubSpot CRM: 6
- Gong call recordings: 4
- Ad platform accounts (Apple Search Ads, Google Ads, Meta Ads): 4
- Attio CRM: 3

10 bots need nothing beyond built-in tools or the Connections catalogue.

## How the bot list was found

- Marketplace pages load their list with JavaScript, so a plain fetch of `/bot/marketplace` returns only the title.
- `https://x.ai/sitemap.xml` lists 91 bot pages. The category pages (`personal`, `marketing`, `product`, `engineering`, `from-grok-bot-team`, `design`, `operations`, `recruiting-people`, `sales`) were fetched with `curl` and their links matched the sitemap, except two bots (`overheard`, `tradbot-2`) that only the sitemap lists.
- Each bot page embeds its instructions, skills, routines and integrations in its page data. That is where the tool lists come from.
- Not checked: bots added after the sitemap was fetched (2026-11-02). Search results showed no bot outside the sitemap.

## Caveats

- Mate text is the bot creator's own text, copied word for word, and credited in **From** and the source link. Added by us: the `# <name>` title, section headings, the `-more` pointer. Three names over Kiro Crew's 24-character limit are shortened (Critiquito, Customer Call Coach, Support Inbox Assistant).
- The text belongs to each bot's creator, credited in **From** and the source link in each file. To have a mate removed, open an issue.
- Tool equivalents were judged from the Kiro Crew docs and the 29-entry Connections catalogue in Kiro Crew 0.13. A `custom-mcp` entry does not promise a vendor MCP server exists.
- Every `.crewjam` passed Kiro Crew's own import checks (`crewmate_bundle.py`).
