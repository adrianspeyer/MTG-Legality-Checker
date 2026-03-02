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
* **Multi-Source Import:** Accepts decklists from MTG Arena, Moxfield, Archidekt, Goldfish, **Decked Builder**, and more — automatically parsing section headers like `Command Zone`, `Creatures(29)`, `Main Deck (99)`, etc.

## 🛠️ How to Use

1. **Download:** Save the `index.html` file to your computer.
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
* **Generic** — `1 Card Name`, `1x Card Name`, or just `Card Name`
* **Double-Faced Cards** — `1 Ojer Taq, Deepest Foundation // Temple of Civilization` (back face stripped for lookup, full name preserved in display and copy)

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

## 📌 Changelog

### v6
* **Double-Faced Card Handling:** Cards with `//` syntax now parse correctly — front face used for Scryfall lookup, full name displayed and preserved when copying.
* **Decked Builder Support:** Parser now recognizes `Command Zone`, `Main Deck (99)`, `Creatures(29)`, `Spells(33)`, `Lands(37)`, and other type/count headers.
* **Separate Copy Buttons:** Legal and illegal cards can now be copied independently.
* **Not Found in Summary:** Cards not found on Scryfall now appear in the legality summary count.

### v5
* Initial public release with legality checking, wildcard calculator, mana curve, and card preview.

## ⚖️ Disclaimer

*This tool is unofficial Fan Content permitted under the Fan Content Policy. Not approved/endorsed by Wizards. Portions of the materials used are property of Wizards of the Coast. ©Wizards of the Coast LLC.*
