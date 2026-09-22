# Changelog

Model version history. Metrics are measured on the sealed 134-night
Challenge-2018 PSG holdout unless noted otherwise. See
[BENCHMARKS.md](BENCHMARKS.md) for evaluation protocol details.

## v4.2.3-dev (2026-09-21)

- Decoder prior weights re-tuned on labeled out-of-fold data.
- Sealed holdout: live causal κ 0.367 / acc 58.6%; offline decode κ 0.390 /
  acc 61.3% (vs κ 0.382 / 56.7% for the previous production model).
- Ring-domain deep-sleep detection regression from the v4.2 campaign fixed;
  all real-device validation nights pass.

## v4.1 (2026-09)

- First sealed-holdout evaluation on the 134-night Challenge-2018 holdout.
