# William Wallace

**Solutions Architect · Full-Stack Builder**

I dig into hard problems, weigh the alternatives, and ship what wins on performance and cost. A decade of turning complex operations into systems that scale, now pointed at software I design, build, and run end to end.

🌐 [williamlwallace.com](https://williamlwallace.com) &nbsp;·&nbsp; ✉️ Contact@williamlwallace.com

---

## Open source

### [Claude Usage Tracker](https://github.com/hamed-elfayome/Claude-Usage-Tracker) &nbsp;·&nbsp; Swift / SwiftUI &nbsp;·&nbsp; 3,000+ stars

Native macOS menu bar app. Credited contributor.

- **Shipped in [v3.2.0](https://github.com/hamed-elfayome/Claude-Usage-Tracker/releases/tag/v3.2.0):** root-caused an `EXC_BAD_ACCESS` crash on macOS 26/27, traced to an unbounded AppKit and SwiftUI layout loop that never converged during the popover's animated resize. Fixed it without regressing the sizing behavior an earlier PR depended on. ([#265](https://github.com/hamed-elfayome/Claude-Usage-Tracker/pull/265))
- **In review:** *Keep Awake*, sleep prevention built on IOKit power assertions, with an idempotent reconcile step, injectable clock and assertion seams for testing, 29 unit tests, and 38 localization keys across 13 languages. ([#282](https://github.com/hamed-elfayome/Claude-Usage-Tracker/pull/282))

I picked up Swift for this project. The interesting part was not the language, it was reading an unfamiliar codebase closely enough to find a bug the maintainers had been living with.

---

## What I build

### [Trendy Tech Tribe](https://trendytechtribe.com)

A technology news and analysis publication covering AI, semiconductors, EVs, energy policy, and markets. Designed, built, and operated solo.

- Static and serverless architecture on Astro, Vercel, and PostgreSQL, with a self-hosted search index, chosen to run at near-zero fixed cost
- A command line toolchain of 40+ tasks covering publishing, verification, translation, and distribution
- An automated editorial pipeline with a multi-model fact-checking gate, extended with corpus-wide link-rot detection and scheduled re-verification so published work stays accurate as its sources decay
- Technical SEO built to spec: structured data, news sitemaps, IndexNow and Bing submission, and search-console data feeding topic selection
- Localized across 13 languages, with validation tooling and hand-checked metadata
- Monetized through display advertising and affiliate placements, including consent management and disclosure compliance

### [williamlwallace.com](https://williamlwallace.com)

Portfolio and personal site. Next.js 16, React 19, Tailwind 4. HMAC-signed session auth with httpOnly cookies and timing-safe comparison, serverless routes backed by Redis, and a hardened header and CSP configuration.

---

## Stack

**Languages** JavaScript · TypeScript · Swift · Python · SQL
**Frontend** React · Next.js · Astro · SwiftUI · Tailwind CSS
**Backend and infra** Node.js · Serverless · PostgreSQL · Redis · Vercel
**Native** Swift · SwiftUI · AppKit · IOKit · XCTest
**Data** GIS and spatial analysis · Data visualization · Analytics
**Practice** System design · Performance and cost optimization · Technical SEO · Security hardening · AI-assisted development

---

## Background

Ten years in public health and state government, most recently leading strategic analysis and systems modernization for five statewide programs, before that running teams and data operations for the CDC's COVID-19 response. That work is where I learned to take an operational mess apart and rebuild it as something that holds.

---

## A note on this profile

Most of what I build lives in private repositories, so the contribution graph here undersells the volume. The public proof is upstream: the pull requests above, and the sites themselves, which are live and running the work described.

---

Outside the terminal: photography, EV technology, and an ongoing argument with my own fitness data.
