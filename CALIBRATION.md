# Calibration

Model: median launch-day curve, calibrated at run time from the case's
own comparables. See the header comment in `main.ts` for the full design.

- Keep only Tier: comparable launches with hour 1 at least 20,000
  viewers and at least 15% of their release-day peak.
- Median log ratio ln(viewers_h / viewers_1) per hour, smoothed over
  neighbouring hours. Median ratios: hour 2 0.88, hour 6 0.95,
  hour 12 0.97, hour 21 2.14, hour 24 1.76.
- Spread: lognormal, sigma 0.18 per square-root hour, wider than the
  house baseline's 0.15.
- Leave-one-out pinball loss on the 15 filtered comparables: baseline
  0.267, this model 0.233, typical miss 45% vs 54%. On 19 comparables:
  baseline 0.40, this model 0.32. True practice answers are not in the
  kit, so those are relative scores on comparables, not practice scores.
