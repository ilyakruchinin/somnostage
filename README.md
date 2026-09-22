# SomnoStage

**On-device sleep staging for [SomnoTrace](https://github.com/ilyakruchinin/SomnoTrace) —
Wake / Light / Deep / REM from a finger pulse oximeter, running entirely on an ESP32-S3.**

SomnoStage is a compact machine-learning model that classifies every 30-second
epoch of a night into Wake, Light, Deep, or REM sleep. It runs on-device inside
SomnoTrace firmware — no cloud, no subscription, no data leaving the hardware —
using continuous finger pulse oximetry (SpO₂), pulse rate, and motion from a
Wellue / O2 Ring–class sensor.

The model operates in two modes:

- **Live** — causal, real-time scoring while the night is in progress
- **Offline** — a post-night decode used when generating reports, which can
  look at the whole night and is slightly more accurate

## Training data

SomnoStage was developed on more than 1,000 expert-scored overnight sleep
recordings — on the order of 700,000 labelled 30-second epochs in the training
pool alone — drawn from multiple independent clinical polysomnography and
wearable cohorts. It was evaluated on a sealed 134-night holdout of subjects
from development cohorts never seen during training or feature selection. All
sources are public research datasets; see [ATTRIBUTIONS.md](ATTRIBUTIONS.md)
for the full list and required citations.

## Accuracy

Measured on a sealed 134-night Challenge-2018 polysomnography holdout
(model **v4.2.3-dev**):

| Mode | Cohen's κ | 4-stage accuracy | Macro F1 |
|---|---:|---:|---:|
| Live on-device (causal) | 0.367 | 58.6% | 0.542 |
| Offline post-night decode | 0.390 | 61.3% | 0.560 |

For 4-stage staging scored against laboratory polysomnography, this places
SomnoStage above most older-generation wrist wearables (Garmin, Polar,
Withings, pre-watchOS 9 Apple Watch — κ ≈ 0.20–0.30), on par with the
WHOOP 4.0 / Galaxy Watch 3 / Fitbit Charge 2 class (κ ≈ 0.37–0.40), and below
current flagships (Apple Watch watchOS 9+ κ ≈ 0.53, Oura Ring Gen 3 κ ≈ 0.65,
Dreem 2 EEG headband κ = 0.74). Two human experts scoring the same PSG agree
at κ ≈ 0.75–0.82 — that is the practical ceiling.

Full comparison table with study citations: [BENCHMARKS.md](BENCHMARKS.md).

## Limitations

- SomnoStage is **not a medical device** and is not a diagnostic tool. Do not
  use it to diagnose or rule out sleep disorders.
- Device comparisons are cross-study, not head-to-head: different cohorts,
  sensors, protocols, and scoring rules. They are indicative only.
- SomnoStage uses finger oximetry + pulse + motion. Most comparators use wrist
  PPG/actigraphy; the best performers add temperature, circadian features, or
  actual EEG.

## License

**Closed source.** The SomnoStage model is proprietary and is *not* covered by
SomnoTrace's GPLv3 license.

- **Official SomnoTrace firmware builds** (from
  [ilyakruchinin/SomnoTrace](https://github.com/ilyakruchinin/SomnoTrace))
  embed the model under a free, non-exclusive, non-transferable,
  non-sublicensable license. It just works — no purchase, no activation.
- **Forks, source builds, and third-party products receive no license and no
  model artifact** by default. Forking SomnoTrace under GPLv3 grants no
  rights in the model. Using the model in anything other than an official
  SomnoTrace build requires a separate license — commercial licenses are
  available.

Full terms: [LICENSE-MODEL.txt](LICENSE-MODEL.txt).
Licensing enquiries: email **somnostage@duck.com** or
[open an issue](https://github.com/ilyakruchinin/somnostage/issues) in this
repository.

## Data attribution

SomnoStage was developed and evaluated using public research datasets
published under ODC-By 1.0, CC BY 4.0, and CC0 licenses. See [NOTICE](NOTICE)
for the required notices and [ATTRIBUTIONS.md](ATTRIBUTIONS.md) for the full
source list and citations.

---

*This repository contains documentation only. The model artifact itself is
distributed exclusively inside official SomnoTrace firmware builds.*
