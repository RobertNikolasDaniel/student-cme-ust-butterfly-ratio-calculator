# Student CME UST Butterfly Ratio Calculator

## Overview

This project is a simplified educational calculator designed to help students understand how U.S. Treasury futures butterflies are structured and balanced using DV01.

The calculator expands on earlier Treasury futures relative value and hedge ratio projects by introducing a third leg to create a DV01-neutral butterfly structure.

Rather than focusing on outright direction in interest rates, a butterfly trade attempts to isolate changes in the *shape* or *curvature* of the Treasury yield curve.

The goal of this sheet is not to replicate an institutional pricing system.

The goal is to build intuition.

---

# What Is a UST Butterfly?

A Treasury butterfly (“fly”) is a three-leg rates trade involving:

- a front wing
- a belly
- a back wing

Example:

- ZF (5Y) = front wing
- ZN (10Y) = belly
- ZB (30Y) = back wing

The “belly” is the middle maturity sector of the curve.

A butterfly trade attempts to express a view on whether the belly sector is:
- rich
- cheap
- overperforming
- underperforming

relative to the two wings.

---

# Core Idea

A DV01-neutral butterfly attempts to remove:
- outright parallel rate exposure

and isolate:
- curve shape changes

In simple terms:

> “I do not care if the entire curve moves up or down together.”

Instead:

> “I care if the middle of the curve behaves differently than the edges.”

---

# What the Calculator Does

The sheet estimates:

1. CTD bond DV01
2. Treasury futures DV01
3. Wing DV01 exposure
4. Belly contracts needed to neutralize the wings
5. Net DV01 of the final structure

This allows students to approximate balanced Treasury futures butterfly structures.

---

# Inputs

Each leg requires:

- Clean Price
- Modified Duration
- Conversion Factor
- Number of Contracts

for:
- Front Wing
- Belly
- Back Wing

---

# How DV01 Is Estimated

The calculator approximates CTD bond DV01 using:

```math
DV01 \approx Price \times ModifiedDuration \times 0.0001 \times 1000
```

Then estimates futures DV01 using:

```math
FuturesDV01 \approx \frac{CTD\ DV01}{ConversionFactor}
```

This is intentionally simplified for educational clarity.

---

# What “Belly Contracts Needed” Means

This is the most important output in the sheet.

The calculator measures:
- the combined DV01 exposure of the front and back wings

Then solves:

> “How many belly contracts are needed to offset and neutralize those wings?”

In other words:

```math
FrontWingDV01 + BackWingDV01 + BellyDV01 \approx 0
```

Example:

If:
- wings together create +$200 DV01
- each belly contract contributes -$50 DV01

then:

```math
200 / 50 = 4
```

So approximately 4 belly contracts are needed to balance the fly.

---

# Why Ratios Matter

Treasury futures are NOT equally sensitive to interest rates.

1 ZB contract does not behave like:
- 1 ZN
- or 1 ZF

because each futures contract inherits:
- duration
- CTD sensitivity
- conversion factor effects

from its underlying deliverable Treasury bond.

The calculator helps approximate the “true balance” between these contracts.

---

# What a Neutral Butterfly Does

A balanced butterfly should theoretically experience minimal P&L impact if:
- the entire yield curve shifts evenly higher
or
- the entire yield curve shifts evenly lower

Instead, the fly primarily responds to:
- curve bending
- sector richness/cheapness
- curvature changes

This is why butterflies are commonly used in:
- Treasury relative value trading
- macro trading
- fixed income positioning
- yield curve analysis

---

# Educational Purpose

This project intentionally simplifies institutional rates mechanics.

It does NOT model:
- repo financing
- delivery optionality
- convexity
- changing CTD dynamics
- funding stress
- liquidity effects
- basis risk

Instead, the calculator is designed to help students visually understand:
- Treasury futures sensitivity
- DV01 balancing
- hedge ratio mechanics
- butterfly structure construction

in a transparent and approachable way.

---

# Example Structures

Possible butterflies include:

- ZF / ZN / ZB
- ZT / ZF / ZN
- ZN / TN / ZB

depending on the maturity sectors being analyzed.

---

# Final Note

This project was built as part of a broader effort to reduce complex fixed income concepts into simple, visually understandable educational tools for students learning Treasury futures and relative value trading.
