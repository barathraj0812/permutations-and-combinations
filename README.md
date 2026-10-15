# P&C Quick Calculator — JEE Mathematics

A single-file, offline calculator for **Permutations, Combinations and Factorials**, built for classroom use on a large touch display (for example a 75" BenQ smartboard). It gives exact answers and shows the identities that connect your input and your result.

- **One file:** `index.html` (HTML + CSS + JavaScript, no libraries, no network needed)
- **Exact arithmetic:** uses BigInt and exact fractions, so there is no rounding

## Features

### Multiple calculators
- **＋ Add Calculator** adds another calculator next to the current one.
- Each calculator is independent, with its own input, keypad, result and identities, so several can be used at the same time.
- ✕ removes a calculator (hidden when only one is left).
- Two calculators sit side by side; more wrap into extra columns or rows and the page scrolls.
- The last calculator you touched has a cyan outline.

### Board and display controls (top bar)
| Control | What it does |
|---|---|
| ☀ Light / ☾ Dark | Switches between light and dark theme |
| ▣ Smartboard | Larger keys, text and answers for a touch board |
| A− / A+ | Scales the whole interface (80% to 150%) |
| ⛶ Fullscreen | Enters or exits fullscreen |

### Input
Type on a keyboard or tap the on-screen keypad. The device keyboard is suppressed on touch screens.

| You can write | Meaning |
|---|---|
| `8C3`, `nCr(8,3)`, `C(8,3)` | Combination 8C3 |
| `7P2`, `nPr(7,2)`, `P(7,2)` | Permutation 7P2 |
| `5H3`, `nHr(5,3)`, `H(5,3)` | Selection with repetition, (n+r−1)Cr |
| `n!` | Factorial |
| `+  −  ×  ÷  ^  ( )` | Arithmetic, exponent and brackets |

- Fractions are kept exact, for example `10C4/10C3 = 7/4`.
- `8C3!` is read as (8C3)!. Write `8C(3!)` if you mean 8C of 3 factorial.

**Keypad extras:** `Ans` inserts the previous answer, ◀ ▶ move the cursor, ⌫ is backspace, Clear empties the input.

**Result buttons:** *Copy Answer* and *Use in Input*.

**Shortcuts:** `Enter` calculates in the focused calculator. `Ctrl + Enter` calculates in the active calculator from anywhere.

### Identities (used as input and shown as output)
Identities work in both directions. If your input matches a pattern, the simplified form appears first in a green **"Your input matches these identities"** group. Every `nCr` result also lists the related forms.

| Identity | Recognised in your input | Shown for a result |
|---|---|---|
| **Symmetry** — nCr = nC(n−r) | – | Yes |
| **Pascal's rule** — nCr + nC(r−1) = (n+1)Cr | `7C3+7C2` → `8C3` (also `7C3+7C4`, `7C3+7C5`, mixed with other terms) | Split and combined forms |
| **Ratio** — nCr ÷ nC(r−1) = (n−r+1)/r | `10C4/10C3` → `7/4`, and the inverted quotient | Both ratio forms |
| **Absorption** — n·(n−1)C(r−1) = r·nCr | `3*6C3` → `6 × 5C2`, and the reverse | Yes |
| **At least one** — 2ⁿ − 1 | `2^5-1`, `2^5`, `5C1+…+5C5`, `5C0+…+5C5` | `nC1+…+nCn = 2ⁿ−1` |
| **With repetition** — (n+r−1)Cr | `5H3` → `7C3` | `nCr` as "n−r+1 items, r with repetition" |

Also shown:
- **nPr:** `r! × nCr`, factorial form, and a recurrence.
- **nCr:** factorial form.
- **nPr ÷ nCr = r!** when n and r match.
- **Factorial:** n! = n × (n−1)!, and 0! = 1.

Identities are shown for the first 3 distinct nPr / nCr / nHr terms in an expression, so the result panel stays readable.

## Limits
- n up to 2000
- Answers up to about 18,000 digits
- Expression length up to 400 characters
- Whole numbers only (no decimal points)
- Errors such as `r > n`, division by zero or too-large results are shown as a message under the input

## Running it
Open `index.html` in any modern browser. No installation, build step or internet connection is needed.

It also deploys as a static page, for example on Cloudflare Pages, by uploading `index.html`.

### Browser support
Use a current Chrome, Edge, Firefox or Safari. The side-by-side layout inside each calculator uses CSS container queries (Chrome 105+, Firefox 110+, Safari 16+). On older browsers each calculator stacks the keypad above the result instead.

## Project structure
```
index.html   the whole app
  ├─ <style>            themes, layout, Smartboard mode
  ├─ <script id="engine">   tokenizer, parser, exact evaluator, identity engine (no DOM)
  └─ <script id="ui">       calculators, keypad, toolbar controls
```

## Credits
© 2026 Barath M · All rights reserved · Chennai, Tamil Nadu, India
