# TetherMax Design System

> Manifest: 37 components · 23 cards · full token system · TetherMax app UI kit. Link `styles.css`; read components off `window.TetherMaxDesignSystem_ad5bd2`.

A complete, code-first design system for **TetherMax** — a crypto-exchange
**cashback & rewards** platform. Users link their exchange UID (Bitget, Bybit, OKX,
Binance, …) and TetherMax rebates a large share of the trading fees they'd otherwise
pay, with cashback **boosts**, **events / prize pools**, leagues and points on top.

The product is a **mobile-first app** (iOS + Android) with companion mobile-web and
desktop-web surfaces, in **Korean and English**. The visual language is a Material-UI
foundation re-skinned with a vivid royal-blue TetherMax brand, glossy 3D reward icons,
and a dense, data-rich layout.

> **Source of truth:** the attached Figma file `추출용.fig` ("for extraction"), 23 pages
> of product flows (login, withdrawal, exchange list, events, global league, partner hub,
> my-page, benefits, cashback summary, points, …). Tokens, components, logos, exchange
> marks and 3D icons in this system were extracted from that file. No live URL or codebase
> was provided; if you have the Figma, treat it as canonical over anything here.

---

## Content fundamentals — how TetherMax writes

- **Voice:** direct, benefit-led, slightly punchy. Leads with the number. The hero line
  literally challenges the user: *"You're paying too many fees. See how much cashback you're missing."*
- **Person:** second person — talks to *you* ("Link your UID", "you save 54%"). Refers to
  itself as TetherMax, not "we".
- **Casing:** Title Case for screen titles & section heads ("All Partner Exchanges",
  "Top Partner Exchanges", "Recent Average Cashback", "Ongoing Events"). Sentence case for
  body and helper text.
- **Numbers are the message.** Savings %, USDT amounts, taker/maker rates and prize pools
  are foregrounded and bolded ("**85%** cashback", "**$100,000.00**", "Final Taker **0.0184%**").
  Currency shown as `$` for fiat-equivalent and `USDT` as a trailing unit.
- **Microcopy is reassuring + precise:** "Pay only $46 instead of $100 in fees and save 54%.",
  "Actual savings may vary depending on your maker/taker ratio."
- **CTAs are short imperatives:** *Join Now, Sign up free, Link UID, Withdraw, Start Tour, View all, See All*.
- **Urgency without hype:** countdowns ("Ends in 45M 37S") and limited-time framing, but no
  exclamation-mark spam.
- **No emoji as UI.** A few playful glyphs appear inside content (🏆 for rewards, 👍 on boost
  badges, medal numbers for rankings) but emoji are never load-bearing chrome. Korean copy uses
  Pretendard; English uses Inter.

## Visual foundations

- **Color.** One dominant brand hue: vivid royal blue. `--tm-blue #0067FF` for actions, links,
  the logo and active states; `--tm-blue-deep #0031C6` for hero/reward surfaces (often as a
  `135deg` gradient, `--gradient-hero`). Everything else is a near-neutral MUI greyscale on a
  **near-white canvas** `--surface-canvas #F8FAFC`; white cards sit on top. Status colors are
  standard MUI: success `#2E7D32`, warning `#EF6C00`, error `#D32F2F`, info `#0288D1`, each with a
  soft tinted background for banners.
- **Type.** **Inter** is the workhorse (UI + body, deliberately small/dense: 10–14px).
  **Plus Jakarta Sans** is the display/heading face for big marketing numbers.
  **Pretendard** carries Korean. Headings are bold (700) with slightly tight tracking;
  body is 400/500; emphasis is 600.
- **Layout.** 8-pt grid (4px half-step). Mobile frame is **375px** wide. Content is
  vertically stacked cards with generous internal padding (16–20px) and 12–16px gaps. Horizontal
  scrollers for "top exchanges" tiles and filter chips. Sticky top header + fixed 5-tab bottom nav.
- **Surfaces / cards.** White, **12–16px** corner radius, soft low-contrast shadow
  (`--shadow-card: 0 2px 12px rgba(93,96,103,.10)`) — *not* heavy borders. An outlined variant
  uses a 1px hairline (`--border-subtle #E6E7E9`) instead of shadow. Bottom sheets / large modals
  go to 16–24px radius.
- **Buttons.** Contained = solid blue, white bold label, ~8px radius, subtle shadow; hover darkens
  (`--color-primary-hover #0059DB`). Outlined = blue 1.5px border on transparent. Text = blue label.
  Full-width inside cards & sheets.
- **Chips.** Pill (`--radius-pill`). Filter bars: active = solid blue, inactive = outlined grey.
  Boost/status chips are small solid color pills ("54%", "85% Boost"); countdown chips are
  orange-on-warning-tint.
- **Imagery.** Two registers: (1) **glossy 3D icons** in a blue→violet gradient (infinity logo,
  trophy, coins, money pocket, confetti) used as reward/celebration accents; (2) **dark event
  banners** — near-black radial gradients with a 3D prop and a big % or prize number. Brand photography
  is cool-toned and high-contrast.
- **Motion.** Restrained and functional. Standard Material easing (`cubic-bezier(.4,0,.2,1)`),
  120–320ms. Toggles slide, sheets/dialogs fade+scale, progress bars animate width. No bouncy or
  decorative looping animation on content.
- **States.** Hover = subtle ink wash `rgba(0,0,0,.04)` (or darker fill on solid buttons).
  Selected = blue tint background `--tm-blue-50` and/or a 1.5px inset blue ring (exchange rows).
  Focus = 3px blue focus ring `--focus-ring`. Disabled = 12% black fill / 38% black text.
- **Transparency & blur.** Light touch — the reward card's withdraw button uses a translucent
  white (`rgba(255,255,255,.16)`) with a small backdrop blur over the gradient; backdrops dim to
  `rgba(0,0,0,.5)`.

## Iconography

- **System:** **Material Symbols, Rounded** weight, used as **24px line icons** in `currentColor`
  (16 / 20 / 24 / 36px sizes exist). This is the entire UI icon vocabulary — back, add, calendar,
  campaign/bell, candlestick chart, account, star, alarm, calculate, analytics, cancel (filled), etc.
- **In this system:** a real extracted subset ships as data in `assets/icons/icon-data.js`, rendered
  with `<Icon name="AddRounded" size={24} />` (names in `assets/icons/Icon.d.ts`). For any glyph not
  in the extracted set, pull it from **Material Symbols Rounded** (Google Fonts) — same family, exact match.
- **Brand marks:** the **∞ infinity** symbol is the TetherMax identity. `<IconTethermaxBi />` is the
  gradient infinity glyph (used in the bottom-nav Home tab & snackbars); `assets/logo/tethermax-wordmark.png`
  is the full "∞ tetherMax" wordmark lockup.
- **Partner exchange logos:** 16 brand marks (Binance, Bybit, OKX, Bitget, Gate, MEXC, KuCoin, BingX,
  BitMart, BitMEX, BloFin, DeepCoin, Houbi, WOO X, Zoomex, Bitvenus) ship as data via
  `<ExchangeLogo name="LogoBybit" size={28} />` (`assets/exchanges/ExchangeLogo.d.ts`).
- **3D icons:** glossy reward icons (`DIconTrophy3`, `DIconMoney3`, `DIconMoneyPocketGold3/Silver3`,
  `DIconConfetti3`, `DIconTethermaxLogo3`) are bitmap components in `assets/3d/` — used for
  celebration / reward moments, never as functional UI icons.
- Emoji are **not** part of the icon system (see Content fundamentals).

---

## Index / manifest

**Global CSS** — consumers link `styles.css` (an `@import` manifest):
- `tokens/fonts.css` — Inter, Plus Jakarta Sans, Pretendard webfonts
- `tokens/colors.css` — brand ramp, neutrals, semantic + aliases (use the `--color-*`/`--text-*`/`--surface-*` aliases)
- `tokens/typography.css` — families, scale, weights + `.tm-*` text helpers
- `tokens/spacing.css` — 8-pt spacing, radii, elevation, motion
- `tokens/fig-tokens.css` — full **926-variable** raw Figma token set, all theme modes (Light/Dark/mobile/desktop…)
- `tokens/base.css` — light reset
- `assets/3d/fig-assets.css` — 3D-icon bitmap classes

**Components** (`window.TetherMaxDesignSystem_ad5bd2`):
- `components/actions/` — **Button**, **IconButton**
- `components/forms/` — **TextField**, **Select**, **Checkbox**, **Radio**, **Switch**, **Slider**
- `components/data-display/` — **Chip**, **Badge**, **Avatar**, **Card**, **Divider**
- `components/feedback/` — **Alert**, **Dialog**, **Snackbar**, **Tooltip**, **LinearProgress**, **CircularProgress**
- `components/navigation/` — **Tabs**, **BottomNav**
- `components/tethermax/` — **RewardCard**, **AppHeader**, **ExchangeRow**, **ExchangeTile**, **EventCard**, **CountdownPill**, **ListRow**

**Assets / generated** — `assets/icons/` (`Icon`), `assets/exchanges/` (`ExchangeLogo`),
`assets/logo/` (`IconTethermaxBi` + wordmark), `assets/3d/` (`DIcon*` 3D bitmaps).

**UI kit** — `ui_kits/tethermax-app/` — interactive mobile-app recreation (login → home,
exchanges, events, point). See its README.

**Guidelines** — `guidelines/*.card.html` — foundation specimen cards (Colors, Type, Spacing, Brand)
surfaced in the Design System tab.

**Other:** `SKILL.md` (Agent-Skill front-matter for download/reuse).
