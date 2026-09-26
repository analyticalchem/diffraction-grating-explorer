# Diffraction Grating Explorer

An interactive, browser-based demonstration of light diffracting from a reflection grating, and of how a grating monochromator selects wavelengths:

**mλ = d(sin θ + sin φ)**

Three laser lines (445, 532 and 632.8 nm) strike a ruled grating and reflect into a fan of diffraction orders. The figure is styled after the chart “Light Diffraction from Grating” in the teaching workbook *Diffraction Grating Light Angles.xlsm*: white incident beam and 0th order, thick, medium and thin lines for the 1st, 2nd and 3rd orders, and dashed lines for negative orders. A white-light source shows each order as a spectrum. An exit slit, with an adjustable physical width, shows which wavelengths reach it, the bandpass in each order and the resolution. A monochromator mode fixes the entrance and exit slits and turns the grating instead.

No build step and no dependencies: plain HTML, CSS and JavaScript in a single file.

## Running it

- **Locally:** open `index.html` in a browser. Double-clicking works.
- **GitHub Pages:** served from the default branch and the `/ (root)` folder at `https://analyticalchem.github.io/diffraction-grating-explorer/`.

## What you can change

| Control | What it does in the model |
|---|---|
| **Incident angle θ** (−80° to 80°) | Angle of the incident beam from the grating normal. Positive is the side the workbook uses. |
| **Groove density** (100–2400 grooves/mm) | Sets the groove spacing d = 1/N. Higher densities spread the orders further, and orders that would need \|mλ/d − sin θ\| > 1 disappear. |
| **Highest order shown** (±1, ±2, ±3) | How many orders are drawn. Line weight marks the order. |
| **Lasers 1–3** (tick box, slider and number box, 200–1100 nm) | Switch each line on or off and set its wavelength. Common lines are named (helium–neon, frequency-doubled Nd:YAG, blue diode and others). Ultraviolet and infrared lines are drawn gray. |
| **White light** (380–780 nm) | Draws every order as a continuous spectrum that dims toward both ends. Where orders overlap their colors add; 1st-order 760–780 nm lands at the same angles as 2nd-order 380–390 nm. |
| **Exit slit** (slit angle φ, −85° to 85°) | Lists the wavelength that reaches the slit in orders 1 to 3, λ = d(sin θ + sin φ)/m. Click or drag in the figure to move it. |
| **Adjustable slit width** (distance L from grating to slit; width w, 0.01–50 mm on a log scale) | Gives the slit an angular width Δφ = 2·tan⁻¹(w/2L), lists the band of wavelengths each order passes, its bandpass Δλ, and the resolution R = λ/Δλ. |
| **Monochromator mode** (grating rotation ±45°, included angle 2K, wavelength at the exit slit) | Fixes the entrance and exit slits and turns the grating. Switching it on keeps the current θ, φ and a flat grating; the rotation slider, or dragging in the figure, turns it from there. Typing a wavelength turns the grating to send that wavelength (1st order) to the exit slit. |
| **Theme** (auto, light, dark) and **Presentation** | Presentation mode enlarges text, controls and the figure’s lines for a projector and, on wide screens, puts the figure beside the controls. |

## The model

```
mλ = d(sin θ + sin φ)        d = 1/N; both angles from the grating normal, φ positive on the incident side
φ  = sin⁻¹(mλ/d − sin θ)      an order exists only when |mλ/d − sin θ| ≤ 1

Exit slit of width w at distance L, perpendicular to the diffracted beam
Δφ = 2·tan⁻¹(w / 2L)
Δλ = d[sin(φ + Δφ/2) − sin(φ − Δφ/2)] / m  ≈  d·cos φ·Δφ / m
R  = λ/Δλ = (sin θ + sin φ) / [sin(φ + Δφ/2) − sin(φ − Δφ/2)]

Monochromator: slits fixed 2K apart, grating turned ψ from the axis that bisects them
θ  = ψ + K,   φ = ψ − K
mλ = 2d·cos K·sin ψ          the sine drive
```

With the workbook values (θ = 3°, 400 grooves/mm) the diffraction angles match column E of the workbook, for example 7.22°, 9.23° and 11.58° for the three lasers in 1st order.

Simplifications worth knowing about:

- The incident beam is treated as a collimated laser, so no entrance-slit image adds to the bandpass.
- Because λ and Δλ both scale as 1/m, R at a fixed slit angle is the same in every order. A narrower slit, a longer distance to the slit or a larger diffraction angle raises it.
- The monochromator is drawn as its geometry only; the collimating and focusing mirrors of a Czerny–Turner layout are left out.
- Relative intensities of the orders (blaze, efficiency) are not modeled. Line weight only marks the order, following the workbook chart.
- Beam colors are approximate screen colors for each wavelength.

## Files

```
index.html    the whole demo: page, styles and script
```

## License

MIT. See [LICENSE](LICENSE).
