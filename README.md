# MTG Arena Deck Analyzer

A lightweight, browser-based tool to check deck legality, calculate wildcard costs, and visualize mana curves for Magic: The Gathering Arena.

## 🚀 Features

* **Arena Legality Check:** Instantly verifies if cards are legal in formats like **Historic Brawl**, **Timeless**, **Explorer**, and **Standard**.
* **"True" Availability Detection:** Smartly detects if a card is actually playable on Arena, even if you paste an older printing (e.g., *Ice Age* Underground River).
* **Wildcard Calculator:** Automatically counts how many **Common**, **Uncommon**, **Rare**, and **Mythic** wildcards you need to craft the deck.
* **Visual Spoiler:** Hover over any card name to see a high-quality image preview that follows your mouse.
* **Mana Curve Analysis:** Visual bar chart showing the deck's mana distribution.
* **Commander Support:** Full support for 100+ card decks using smart batch processing.
* **Export Clean Lists:** Separate copy buttons for **legal** and **illegal** cards, formatted for MTG Arena import.
* **Double-Faced Card Support:** Properly handles cards with `//` syntax (e.g., *Ojer Taq, Deepest Foundation // Temple of Civilization*), displaying the full name while looking up the front face.
* **Multi-Source Import:** Accepts decklists from MTG Arena, Moxfield, Archidekt, Goldfish, **Decked Builder**, **ManaBox**, and more — automatically parsing section headers, set codes, and type/count labels.

## 🛠️ How to Use

1. **Download:** Save the `index.html` file to your computer (you can rename it to whatever you like).
2. **Run:** Double-click the file to open it in any modern web browser (Chrome, Firefox, Edge, Safari).
3. **Paste:** Copy your decklist from sites like Moxfield, Archidekt, Goldfish, or Decked Builder and paste it into the text area.
4. **Analyze:** Select your format (e.g., Historic Brawl) and click **Analyze**.
5. **Copy:** Use **Copy Legal** to grab your legal cards for Arena import, or **Copy Illegal** to review problem cards separately.

## 📋 Supported Formats

The tool currently checks legality against the following Arena formats:

* Historic Brawl
* Standard Brawl
* Timeless
* Historic
* Explorer
* Standard
* Alchemy

## 📥 Supported Import Formats

The parser handles a variety of decklist formats:

* **MTG Arena** — `Commander` / `Deck` / `Sideboard` headers
* **Decked Builder** — `Command Zone`, `Main Deck (99)`, `Creatures(29)`, `Spells(33)`, `Lands(37)`, `Sideboard (4)`
* **ManaBox** — `//Commander` / `//Deck` / `//Sideboard` headers, with `(SET) 123` collector info stripped automatically
* **Generic** — `1 Card Name`, `1x Card Name`, or just `Card Name`
* **Double-Faced Cards** — `1 Ojer Taq, Deepest Foundation // Temple of Civilization` (back face stripped for lookup, full name preserved in display and copy)

## 🔒 Security

* **Content Security Policy (CSP):** Embedded meta tag restricts all resource loading to known-safe origins. Works on GitHub Pages, local file, or any static host — no server config needed.
* **XSS Prevention:** Zero `innerHTML` calls with user or API data; all dynamic content uses safe DOM APIs.
* **Input Validation:** Decklist size, card count, name length, and quantity are all bounded to prevent abuse.
* **URL Allowlisting:** Only HTTPS URLs from `cards.scryfall.io` and `c1.scryfall.com` are loaded as images.
* **No Global State:** All application state is encapsulated in an IIFE closure.

## 🔧 Technical Details

* **No Server Required:** Runs entirely in your browser using client-side JavaScript.
* **API:** Powered by the [Scryfall API](https://scryfall.com/docs/api).
* **Batch Processing:** Uses Scryfall's Collection API to fetch data in chunks of 75, ensuring large Commander decks load in under a second without hitting rate limits.

## 📝 Example Decklist Format

The tool accepts standard text exports:

```text
Commander
1 Atraxa, Praetors' Voice

Deck
1 Sol Ring
1 Arcane Signet
1 Swords to Plowshares
3 Swamp
3 Island
```

And Decked Builder exports:

```text
Command Zone
Giada, Font of Hope

Main Deck (99)

Creatures(29)
1 Angel of Sanctions
1 Ojer Taq, Deepest Foundation // Temple of Civilization

Spells(33)
1 Sol Ring
1 Path to Exile

Lands(37)
30 Snow-Covered Plains

Sideboard (4)
1 Deep Gnome Terramancer
```

And ManaBox exports:

```text
//Commander
1 Giada, Font of Hope (SNC) 14

//Deck
1 Angel of Sanctions (AKR) 1
1 Sol Ring (CMR) 472
1 Ojer Taq, Deepest Foundation // Temple of Civilization (LCI) 27
30 Snow-Covered Plains (KHM) 277

//Sideboard
1 Deep Gnome Terramancer (CLB) 658
```

## 📌 Changelog

### v7
* **Security Hardening:** All dynamic content rendering replaced with safe DOM construction (`createElement` / `textContent`) to eliminate XSS vectors from API responses or crafted decklists.
* **Content Security Policy:** Added CSP meta tag restricting image sources to Scryfall domains, API connections to `api.scryfall.com`, and blocking all external scripts, fonts, objects, and form actions.
* **Image URL Validation:** Card preview images are validated against a Scryfall domain allowlist before rendering.
* **API Response Validation:** Scryfall responses checked for expected data shapes before property access.
* **Input Abuse Prevention:** Decklist input capped at 50 KB, max 500 card entries, card names limited to 200 characters, quantities clamped to 1-999, and a 2-second debounce on the Analyze button.
* **No Global State Leakage:** All JavaScript wrapped in an IIFE; `window._legalCards` / `window._illegalCards` no longer exposed.
* **Inline Handlers Removed:** All `onclick` attributes replaced with `addEventListener` bindings.
* **Clipboard Error Handling:** Copy buttons gracefully handle clipboard failures with a fallback message.
* **Referrer Policy:** Added `no-referrer` meta tag to prevent leaking page URLs to external services.
* **Keyboard Shortcut:** Ctrl+Enter triggers analysis from the textarea.

### v6
* **Double-Faced Card Handling:** Cards with `//` syntax now parse correctly — front face used for Scryfall lookup, full name displayed and preserved when copying. Fixed map lookup so DFCs resolve properly against Scryfall's full card names.
* **Decked Builder Support:** Parser now recognizes `Command Zone`, `Main Deck (99)`, `Creatures(29)`, `Spells(33)`, `Lands(37)`, and other type/count headers. Filters out "Built with Decked Builder" signature line.
* **ManaBox Support:** Recognizes `//Commander`, `//Deck`, `//Sideboard` section headers and strips `(SET) 123` collector info from card lines.
* **Separate Copy Buttons:** Legal and illegal cards can now be copied independently.
* **Not Found in Summary:** Cards not found on Scryfall now appear in the legality summary count.

### v5
* Initial public release with legality checking, wildcard calculator, mana curve, and card preview.

## ⚖️ Disclaimer

*This tool is unofficial Fan Content permitted under the Fan Content Policy. Not approved/endorsed by Wizards. Portions of the materials used are property of Wizards of the Coast. ©Wizards of the Coast LLC.*
