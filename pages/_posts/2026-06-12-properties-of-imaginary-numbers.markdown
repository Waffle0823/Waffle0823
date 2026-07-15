---
layout: post
title: "Exploring the Properties of Imaginary Numbers"
date: 2026-06-12 21:00:00 +0900
categories: [math, python, complex-numbers]
type: Article
excerpt: "Visualizing what happens when you raise a complex number to higher and higher powers — spirals, geometric growth, and De Moivre's theorem in action."
---

As a small side project I've been poking at the properties of imaginary numbers over in my [math-projects](https://gitlab.waffly.xyz/waffle/math-projects) repository. The first thing I wanted to *see* — not just prove — is what happens when you keep raising a complex number to higher powers.

## The setup

Take any complex number `z = a + bi`. Instead of thinking of it as a pair of numbers, write it in **polar form**:

```
z = r·(cos θ + i·sin θ)
```

where `r = |z|` is the magnitude (distance from the origin) and `θ = arg(z)` is the angle it makes with the real axis.

## Raising it to the n-th power

When you compute `z¹, z², z³, …` and plot each result on the complex plane, a clear pattern appears. Each power **rotates by θ and scales by r**:

```
zⁿ = rⁿ·(cos nθ + i·sin nθ)
```

This is **De Moivre's theorem**, and two properties fall straight out of it:

- **The angle multiplies:** `arg(zⁿ) = n·θ`. Every step turns by the same angle, so the points trace a spiral around the origin.
- **The magnitude grows geometrically:** `|zⁿ| = |z|ⁿ = rⁿ`. On a log scale this is a perfectly straight line.

So the behavior depends entirely on `r`:

- `r > 1` → the spiral flies outward
- `r < 1` → it winds inward toward 0
- `r = 1` → it stays on the unit circle forever, just rotating

## Seeing it

The [script](https://gitlab.waffly.xyz/waffle/math-projects/-/blob/main/complex-numbers/exponentiations.py) takes a real part, an imaginary part, and a number of iterations, then draws two views with `matplotlib`:

1. The **complex plane** — each `zⁿ` as an arrow from the origin, overlaid on the continuous curve `zᵗ`, which reveals the underlying smooth spiral the discrete powers sit on.
2. The **magnitude plot** — `|zⁿ|` against `n`, compared to `rⁿ`, confirming the geometric growth.

```python
z = complex(real_number, imaginary_number)
values = [z**power for power in range(1, iterations + 1)]

r = abs(z)             # magnitude
theta = np.angle(z)    # argument (angle)
```

## Takeaway

Multiplying complex numbers isn't mysterious once you look at it geometrically: **multiplication rotates and scales**. Repeated multiplication just does the same rotation and scaling over and over, which is exactly why the powers of a complex number spiral. Imaginary numbers stop feeling "imaginary" the moment you plot them.
