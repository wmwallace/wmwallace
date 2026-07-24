<img src="https://raw.githubusercontent.com/wmwallace/wmwallace/main/banner.svg" alt="William Wallace, Solutions Architect. I dig into hard problems, weigh the alternatives, and ship what wins on performance and cost." width="100%" />

<br />

[**williamlwallace.com**](https://williamlwallace.com) &nbsp;·&nbsp; [**trendytechtribe.com**](https://trendytechtribe.com) &nbsp;·&nbsp; [Contact@williamlwallace.com](mailto:Contact@williamlwallace.com)

---

## Shipped upstream

### [Claude Usage Tracker](https://github.com/hamed-elfayome/Claude-Usage-Tracker) &nbsp; [![stars](https://img.shields.io/github/stars/hamed-elfayome/Claude-Usage-Tracker?style=flat-square&label=stars&color=00f0ff&labelColor=09090b)](https://github.com/hamed-elfayome/Claude-Usage-Tracker)

Credited contributor to a native macOS menu bar app in Swift and SwiftUI.

> Popover layout-recursion crash on macOS 26/27 (PR #265): native popover animation fed an unbounded layout loop; replaced with a SwiftUI entrance animation + click-race debounce. Thanks **@Leewallace017**
>
> <sub>Upstream <a href="https://github.com/hamed-elfayome/Claude-Usage-Tracker/releases/tag/v3.2.0">v3.2.0</a> release notes</sub>

<details>
<summary><b>How the crash was found</b></summary>

<br />

Clicking the menu bar icon crashed the app with `EXC_BAD_ACCESS` on macOS 26/27. The main thread was overflowing its stack in an AppKit and SwiftUI layout loop that never converged:

```
NSPopover.show
  └─ NSHostingView.windowDidLayout
       └─ updateAnimatedWindowSize
            └─ _NSPopoverWindow.setFrame:display:
                 └─ layout   (repeats ~6,500x)  →  stack overflow
```

The popover's hosting controller used `sizingOptions = .preferredContentSize`, added earlier to fix positioning, which continuously re-pushed the SwiftUI content size into the window. Paired with `NSPopover.animates = true`, the newer SwiftUI never settled the animated resize.

The fix disables the native popover animation so the resize cannot feed the loop, leaves the earlier sizing work intact, and replaces the motion with a SwiftUI fade and scale entrance that runs purely as a transform on a fixed-size view. A dismiss and re-open race in the click handler got a debounce on the way through.

</details>

<details>
<summary><b>Keep Awake</b> &nbsp;·&nbsp; in review (<a href="https://github.com/hamed-elfayome/Claude-Usage-Tracker/pull/282">#282</a>)</summary>

<br />

Sleep prevention so long agent runs do not die when the Mac idles. Built on a single named IOKit power assertion with one idempotent `reconcile()` owning create and release, so the kernel drops it automatically if the app exits.

- Auto mode driven by real session activity, with a configurable wind-down
- Injectable clock and assertion seams, so the state machine is testable without waiting on real time
- 29 unit tests: timer expiry, wind-down, crashed-session sweep, persistence round-trips
- 38 localization keys across all 13 supported languages

</details>

<sub>Also in review: session-naming fixes for the notch UI (<a href="https://github.com/hamed-elfayome/Claude-Usage-Tracker/pull/284">#284</a>).</sub>

---

## Building now

### Kelvin &nbsp; <sub>private · pre-alpha</sub>

A local-AI photo editor for macOS. A small vision model reads the photograph on-device, then a deterministic engine turns what it saw into three or four fully-formed candidate edits you choose between. No cloud, no account, nothing uploaded.

| | |
|---|---|
| **Pipeline** | Decode once per file, keep everything interactive on a proxy, go full-resolution only on export — a 45 MP RAW stays responsive |
| **Candidates** | Four options render as parameter swaps against a texture already on the GPU, so generating them is nearly free |
| **Performance** | Brush-stroke rendering cut from 17.3 ms to 0.8 ms per frame |
| **Division of labour** | The model makes categorical judgments only. Every number comes from a deterministic, unit-tested engine that can be benchmarked against baselines |

<sub>Swift · SwiftUI · MLX (Qwen2.5-VL) · Core Image · Metal · SQLite</sub>

---

## Built and running

### [Trendy Tech Tribe](https://trendytechtribe.com)

A technology publication covering AI, semiconductors, EVs, energy, and markets. Designed, built, and operated solo. The site is the surface; the engineering is everything holding it up.

| | |
|---|---|
| **Architecture** | Static and serverless on Astro, Vercel, and PostgreSQL with a self-hosted search index, chosen to run at near-zero fixed cost |
| **Editorial** | Every article clears verification before it publishes, and published work is re-checked as its sources change |
| **Scale** | 13 languages, full-text search, PWA, multi-channel distribution |
| **Reach** | Structured data, news sitemaps, and search-console analysis driving discovery |
| **Revenue** | Display and affiliate monetization, with consent management and disclosure compliance |

### [williamlwallace.com](https://williamlwallace.com)

Portfolio and résumé. Next.js 16, React 19, Tailwind 4. HMAC-signed session auth with httpOnly cookies and timing-safe comparison, serverless routes backed by Redis, and a `default-src 'self'` Content-Security-Policy with HSTS and `frame-ancestors 'none'`.

---

## Stack

| | |
|---|---|
| **Languages** | TypeScript · JavaScript · Swift · Python · SQL |
| **Frontend** | React · Next.js · Astro · SwiftUI · Tailwind CSS |
| **Backend** | Node.js · Serverless · PostgreSQL · Redis · Vercel |
| **Native** | Swift · SwiftUI · AppKit · IOKit · Core Image · Metal · XCTest |
| **On-device AI** | MLX · Vision-language models · Local inference · Evaluation harnesses |
| **Data** | GIS and spatial analysis · Data visualization · Analytics |
| **Practice** | System design · Performance and cost optimization · Technical SEO · Security hardening |

---

## Background

Six years in public health and state government. Currently leading strategic analysis and systems modernization across five statewide programs at Washington State Parks; before that, a team lead at the CDC's Seattle Quarantine Station through the COVID-19 response.

That work is where I learned to take an operational mess apart and rebuild it as something that holds.

<details>
<summary><sub>A note on this profile</sub></summary>

<br />

Most of what I build lives in private repositories, so the contribution graph here undersells the volume. The public proof is upstream: the pull requests above, and the sites themselves, which are live and running the work described.

</details>
