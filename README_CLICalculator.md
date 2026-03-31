# CLI Calculator

> Expression-based command-line calculator with clean I/O and robust error handling.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-green?style=flat)

---

## Overview

Most beginner calculator projects ask for three separate inputs (num1, operator, num2). This one doesn't. You type a natural expression like `5 + 3` and get an answer — the way a calculator should work. Built to demonstrate clean Python structure: regex-based parsing, typed function signatures, proper exception handling, and readable output.

---

## Features

- **Expression input** — type `12.5 * 4` as a single line, no multi-prompt flow
- **All four operators** — `+`, `-`, `*`, `/` (also accepts `x` for multiply)
- **Negative number support** — handles `-5 + 3` and `10 / -2`
- **Proper exceptions** — `ZeroDivisionError` and `ValueError` caught and reported cleanly
- **Smart output formatting** — `5.0` displays as `5`, not a bare float
- **Zero dependencies** — Python stdlib only

---

## Tech Stack

| Layer      | Technology       |
|------------|------------------|
| Language   | Python 3.10+     |
| Parsing    | `re` (regex)     |
| I/O        | `input()` / `print()` |

---

## Getting Started

```bash
git clone https://github.com/yourusername/cli-calculator
cd cli-calculator
python calculator.py
```

**Requirements:** Python 3.10 or higher. No pip installs needed.

---

## Example Usage

```
┌─────────────────────────────┐
│     CLI Calculator v2.0     │
│  Enter: 5 + 3 | quit: exit  │
└─────────────────────────────┘

  › 100 / 4
  = 25

  › 12.5 * 8
  = 100

  › 9 / 0
  ✗ Cannot divide by zero.

  › hello + world
  ✗ Invalid expression. Use format: 5 + 3

  › exit
  Goodbye.
```

---

## Engineering Highlights

**Single-line expression parsing**
Instead of prompting three times per calculation, a single `re.match()` call extracts both operands and the operator from a free-text input. The regex handles optional leading signs, decimal numbers, and surrounding whitespace — making the interaction feel natural.

```python
pattern = r'^(-?\s*[\d.]+)\s*([+\-*/])\s*(-?\s*[\d.]+)$'
```

**Result formatting**
`format_result()` checks whether the float result equals its integer cast — if so, it returns the integer string. This avoids cluttering the output with `5.0` or `100.0` when the answer is whole.

**Graceful error surface**
Only two exception types are ever shown to the user: `ValueError` for bad input and `ZeroDivisionError` for division by zero. All other exceptions bubble up normally, keeping the error surface minimal and honest.

**`x` as multiply alias**
A single `.replace('x', '*')` before parsing handles the common human habit of writing `3 x 4` — a small UX touch that costs nothing.

---

## Roadmap

- [ ] Multi-operator expression support (`5 + 3 * 2`)
- [ ] Calculation history with `history` command
- [ ] Variable storage (`x = 5`, then use `x` in expressions)
- [ ] Unit conversion mode
