# /uk: a Claude Code skill that makes a UK version of your email or web page

US copy, US prices and US delivery rules do not work on a UK audience. `/uk` takes the email or web-page design you have selected and makes a UK-localised copy of it. Your original stays untouched.

<p align="center">
  <img src="assets/uk-cover.png" alt="/uk, UK localisation, for emails and web pages" width="560">
</p>

## What you get

Select an email or web-page design, run `/uk`, and Claude:

- **Duplicates the design** next to the original and names the copy "UK email" or "UK web page"
- **Adapts the wording** from US to natural UK English, keeping meaning and tone
- **Converts prices** from US dollars to British pounds with a real, dated exchange rate, not a swapped symbol
- **Updates the free-delivery message** to the UK threshold of £150
- **Flags anything it should not guess**, such as sizing, tax claims and legal terms
- **Keeps your design intact**: typography, styling, images, component links and layout

## Preview

Wording changes the way a UK shopper would expect to read it. Clothing "pants" always become "trousers".

<p align="center">
  <img src="assets/uk-wording.png" alt="US to UK wording: Colorways to Colourways, Favorites to Favourites, Pants to Trousers" width="560">
</p>

Prices are converted, not relabelled. A $198 product becomes £148.38 at an example rate of $1 = £0.7494, and the free-delivery threshold moves from $200 to a fixed £150.

<p align="center">
  <img src="assets/uk-pricing.png" alt="$198 becomes £148.38 at an example rate, and free delivery over $200 becomes free delivery over £150" width="560">
</p>

## Why

The quick way to localise is to find and replace. It leaves "color" in the headline, puts a £ sign in front of a dollar amount and keeps a $200 delivery threshold that means nothing in the UK. None of it looks broken, so it ships.

`/uk` does the whole job and shows its working. It reports the exchange rate, the date and the source, and it marks converted prices as exchange-rate conversions rather than confirmed UK retail prices.

## How it handles prices

- **UK prices you supply win.** If you have approved UK prices, it uses them.
- **Otherwise it converts.** It uses the rate you give it, or the latest dated USD-to-GBP rate from a reliable source. GBP = original USD amount × GBP per USD, rounded once to two decimal places.
- **It never just swaps the symbol.** If you are fixing an earlier symbol-only localisation, it goes back to the original USD amounts, not the relabelled pound amounts.
- **No reliable rate? It asks you for one.**
- **The £150 free-delivery threshold is a supplied policy.** It is not an exchange-rate conversion.

## Install

This is a personal skill, so install it once and it works in every project.

```bash
git clone https://github.com/JDebDesign/claude-code-uk-skill.git
mkdir -p ~/.claude/skills
cp -R claude-code-uk-skill/skills/uk ~/.claude/skills/uk
```

Start a new Claude Code session so it picks the skill up.

To use it in a single project only, copy the `skills/uk` folder into that project's `.claude/skills/` folder instead.

## Use

1. Connect Claude Code to your design tool, with the email or web page selected.
2. Type `/uk`.
3. Review the UK copy. Claude links to it and lists what still needs a human decision.

You can add details in the same message, for example your own exchange rate or approved UK prices.

## Good to know

- It never edits your original. The UK version is a separate copy.
- It does not invent UK sizes, destinations, addresses, tax claims, legal terms or other commercial policies. It flags them for you to confirm.
- Dates, measurements, sizing, URLs and regional terms are reviewed, and dates use an unambiguous UK format where possible.
- Longer UK copy is checked so it stays readable, with no clipping or overlap.
- The skill is a short plain-text file. To change the free-delivery threshold or the wording rules, open `skills/uk/SKILL.md`.

## Also on Figma Community

Prefer to install it from Figma? It is published here: [UK Localisation on Figma Community](https://www.figma.com/community/skill/163358/uk-localisation).

## License

MIT. See [LICENSE](LICENSE).
