---
name: uk
description: Make a UK-localised copy of an email or web page, whether it is a design on a canvas (Figma, Claude Design) or code (HTML, JSX, templates, i18n files).
---

# UK email and web-page localisation

Apply this same workflow to emails and web pages, in any tool.

## 1. Detect the medium

Work out what you have been given, then follow the matching copy rule in step 2.

- **Canvas design**: a selected frame or layer in a design tool such as Figma or Claude Design.
- **Code**: HTML, CSS, JSX or TSX, Vue or Svelte, email templates, or i18n and locale files, in a project or pasted in.
- **Plain text**: copy pasted into the chat with no files.

If it is unclear, ask which one before changing anything.

## 2. Make a copy, never edit the original

- **Canvas design**: inspect the selection and its text. Duplicate it beside the original, leave the original unchanged, and name the copy “UK email” or “UK web page”, as appropriate.
- **Code**: leave the original files unchanged and write UK versions as new sibling files, for example `page.html` becomes `page.uk.html` and `Welcome.tsx` becomes `Welcome.uk.tsx`. If the project already has i18n, add an `en-GB` locale file instead of copying components. Never overwrite a file.
  - **Git branch**: if the project is a git repository, create a branch named `uk-localisation` (add a suffix such as `-2` if that name is taken) before writing the UK files, and commit only the UK files there, with a short message. Never stage or commit the user's other uncommitted changes. Never push, merge or delete branches. If the project is not a git repository, skip this and just write the sibling files.
- **Plain text**: return the UK version below the original, clearly labelled.

## 3. Wording

Adapt US spelling and terminology to natural UK English, preserving meaning and tone. Always replace clothing “pants” or “pant” with “trousers”, matching capitalisation. Use “colourways”, “favourites” and “delivery” where appropriate.

In code, change visible text only: headings, body copy, buttons, labels, alt text, titles, email subject lines and preheaders. Never rename anything the code depends on. That includes CSS properties (`color` stays `color`), class names, IDs, props, variables, function names, API fields, file names, URLs and `href` values, and template syntax and merge tags such as `{{ first_name }}`. Do not run a blanket find and replace.

## 4. Prices

Convert product prices from US dollars to British pounds, not euros. Use approved UK prices if supplied; otherwise use the user's supplied exchange rate or obtain the latest available dated USD-to-GBP rate from a reliable source. Calculate GBP = original USD amount × GBP per USD and round once to two decimal places. Never just replace the symbol. Report the rate, date and source, and identify calculated prices as exchange-rate conversions rather than confirmed UK retail prices. If no reliable rate is available, ask for one. When correcting a previous symbol-only localisation, use the original USD amounts, not the relabelled pound amounts.

In code, if prices come from a data file, API or CMS, convert them at that source or flag that the source needs UK prices. Do not hardcode converted numbers into templates that read from a source. Format currency with the platform, for example `Intl.NumberFormat('en-GB', { style: 'currency', currency: 'GBP' })`, rather than typing the £ sign into every string.

## 5. Delivery

The US free-delivery threshold is $200; the UK threshold is a fixed £150. Use £150 in the UK delivery announcement. This is a supplied regional policy, not an exchange-rate conversion. In code, put it in one named constant or config value, or update the single existing one, instead of repeating it.

## 6. Regional details

Review dates, measurements, sizing, URLs and regional terms. Use unambiguous UK date formatting where possible. In code, prefer `toLocaleDateString('en-GB')` or `Intl.DateTimeFormat('en-GB')` over hand-typed dates, and set `lang="en-GB"` on the page or email root. Do not invent UK sizes, destinations, addresses, tax claims, legal terms or other commercial policies; flag anything requiring confirmation. In emails, flag the legal footer and unsubscribe text for review rather than rewriting them.

## 7. Check the result

- **Canvas design**: preserve typography, styling, images, component links and layout. Check that longer copy remains readable without clipping or overlap.
- **Code**: confirm only text changed. Run the project's build, typecheck or tests if it has them, and report the result. If you can render the page, check that longer UK copy does not clip or break the layout.

## 8. Report

Summarise the changes and flag outstanding regional details.

- **Canvas design**: link to the UK copy.
- **Code**: list each new file with a one-line summary of what changed, and show the exchange rate, date and source used for any converted price. If you created a branch, give its name and the command to go back to the previous branch.
