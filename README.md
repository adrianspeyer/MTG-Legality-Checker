Here is a professional `README.md` file you can include with your project. It documents all the features we built, including the latest additions like the wildcard calculator and mouse-follow card previews.

---

# MTG Arena Deck Analyzer

A lightweight, browser-based tool to check deck legality, calculate wildcard costs, and visualize mana curves for Magic: The Gathering Arena.

## 🚀 Features

* **Arena Legality Check:** Instantly verifies if cards are legal in formats like **Historic Brawl**, **Timeless**, **Explorer**, and **Standard**.
* **"True" Availability Detection:** Smartly detects if a card is actually playable on Arena, even if you paste an older printing (e.g., *Ice Age* Underground River).
* **Wildcard Calculator:** Automatically counts how many **Common**, **Uncommon**, **Rare**, and **Mythic** wildcards you need to craft the deck.
* **Visual Spoiler:** Hover over any card name to see a high-quality image preview that follows your mouse.
* **Mana Curve Analysis:** Visual bar chart showing the deck's mana distribution.
* **Commander Support:** Full support for 100+ card decks using smart batch processing.
* **Export Clean Lists:** One-click button to copy only the *legal* cards to your clipboard, formatted specifically for MTG Arena import.

## 🛠️ How to Use

1. **Download:** Save the `mtg_analyzer.html` file to your computer.
2. **Run:** Double-click the file to open it in any modern web browser (Chrome, Firefox, Edge, Safari).
3. **Paste:** Copy your decklist from sites like Moxfield, Archidekt, or Goldfish and paste it into the text area.
4. **Analyze:** Select your format (e.g., Historic Brawl) and click **Analyze**.

## 📋 Supported Formats

The tool currently checks legality against the following Arena formats:

* Historic Brawl
* Standard Brawl
* Timeless
* Historic
* Explorer
* Standard
* Alchemy

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

## ⚖️ Disclaimer

*This tool is unofficial Fan Content permitted under the Fan Content Policy. Not approved/endorsed by Wizards. Portions of the materials used are property of Wizards of the Coast. ©Wizards of the Coast LLC.*
