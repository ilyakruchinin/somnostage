# SomnoStage accuracy & device comparison

How SomnoStage (v4.2.3-dev) compares with commercial wearables and clinical
devices on **4-stage sleep staging** (Wake / Light / Deep / REM) scored against
laboratory polysomnography (PSG), the clinical gold standard.

## SomnoStage results

Evaluated on a **sealed 134-night Challenge-2018 PSG holdout** — nights never
used in training:

| Evaluation | Cohen's κ | Accuracy | Macro F1 | Notes |
|---|---:|---:|---:|---|
| Live causal argmax | 0.367 | 58.6% | 0.542 | Zero future lookahead — the real-time firmware path |
| Offline forward-backward decode | 0.390 | 61.3% | 0.560 | Post-night decode used for reports; Deep recall 67% |
| Out-of-fold CV (training pool) | 0.392 | 62.3% | 0.559 | 779 nights, per-night grouped — indicative only |

### How to read Cohen's κ

Cohen's kappa measures agreement above chance. Because "Light" dominates a
typical night (~50–60%), raw accuracy alone is misleading — a model guessing
"asleep" all night scores ~85% on 2-state detection. For 4-stage staging:

| κ range | Meaning |
|---|---|
| < 0.20 | Slight — barely better than actigraphy |
| 0.21–0.40 | Fair — typical consumer wearables (**SomnoStage: 0.37–0.39**) |
| 0.41–0.60 | Moderate — solid commercial grade |
| 0.61–0.80 | Substantial — multi-sensor flagships, dry EEG |
| 0.75–0.82 | **Human ceiling** — two sleep physicians scoring the same PSG |

## Comparison table

Compiled from peer-reviewed PSG validation studies (references below).
Ascending order of agreement:

| Standing | Device | κ | Accuracy | Sensors | Study |
|---|---|---:|---:|---|---|
| Below | Apple Watch Series 6 (watchOS 7/8) | 0.20 | ~53% | Accel + PPG | Miller et al. 2022 [1] |
| Below | Garmin Vivosmart 4 | 0.21 | ~50% | Accel + PPG | Stone et al. 2020 [2] |
| Below | Withings ScanWatch | 0.22 | ~53% | Accel + PPG + SpO₂ | Laurent et al. 2021 [3] |
| Below | Garmin Fenix 5S | 0.23 | ~51% | Accel + PPG | Chinoy et al. 2021 [4] |
| Below | Garmin Forerunner 245 | 0.25 | ~50% | Accel + PPG | Miller et al. 2022 [1] |
| Below | Polar Vantage V | 0.28 | ~52% | Accel + PPG | Miller et al. 2022 [1] |
| Below | Polar A370 / Ignite | 0.30 | ~55% | Accel + PPG | Pesonen & Kuula 2020 [5] |
| **★** | **SomnoStage v4.2.3 — live causal** | **0.367** | **58.6%** | 1 Hz SpO₂ + PR + motion | this document |
| On par | WHOOP 4.0 (independent lab) | 0.37 | ~60% | Accel + PPG + temp | Berryhill et al. 2023 [6] |
| On par | Samsung Galaxy Watch 3 | 0.38 | 65.1% | Accel + PPG | Turner et al. 2021 [7] |
| On par | Fitbit Charge 2 / Alta HR | 0.38–0.40 | ~61% | Accel + PPG | de Zambotti et al. 2018 [8] |
| **★** | **SomnoStage v4.2.3 — offline decode** | **0.390** | **61.3%** | 1 Hz SpO₂ + PR + motion | this document |
| Above | Fitbit Charge 4 / Charge 5 | 0.40–0.41 | ~63% | Accel + PPG + SpO₂ | Haghayegh et al. 2020 [9] |
| Above | Fitbit Sense / Versa 3 | 0.42 | ~64% | Accel + multi-path PPG | Stucky et al. 2021 [10] |
| Above | Oura Ring Gen 2 | 0.43 | ~62% | Finger PPG + accel + temp | Miller et al. 2022 [1] |
| Above | WHOOP 3.0 | 0.44 | ~60% | Accel + PPG | Miller et al. 2022 [1] |
| Above | Somfit (Compumedics) | 0.52 | 65.0% | Forehead PPG + movement | Miller et al. 2022 [1] |
| Above | Apple Watch 8/9 (watchOS 9+) | 0.53 | ~70% | High-res accel + multi-LED PPG | Apple validation [11] |
| Above | Oura Ring Gen 3 (OSSA 2.0) | 0.65 | 79.0% | Finger PPG + HRV + circadian + temp | Altini & Kinnunen 2021 [12] |
| Above | Dreem 2 headband | 0.74 | 83.5% | 5-lead dry EEG | Arnal et al. 2020 [13] |
| Ceiling | Human expert consensus (2 scorers) | 0.75–0.82 | 82–85% | Full clinical PSG | Rosenberg & Van Hout 2013 [14] |

## Caveats — read before quoting these numbers

- **Cross-study, not head-to-head.** The commercial-device figures come from
  different studies with different cohorts (mostly healthy adults vs.
  SomnoStage's apnea-enriched clinical holdout), different epoch protocols,
  and different scoring rules. They are indicative, not a controlled trial.
- **Different sensors.** SomnoStage uses continuous 1 Hz finger SpO₂ + pulse
  rate + motion. Most comparators use wrist PPG/actigraphy; the strongest
  performers add temperature, circadian context, or EEG. Finger pulse has a
  real signal-quality advantage over wrist PPG; EEG is a different modality
  entirely.
- **Live vs offline.** The live causal path (κ 0.367) is what runs during the
  night on-device; the offline decode (κ 0.390) runs post-night for reports.
  Both are disclosed because they are not interchangeable.
- **Not a medical device.** These metrics describe agreement with PSG
  scoring, not diagnostic capability.

## References

1. Miller, D. J., Sargent, C., & Roach, G. D. (2022). *A Validation of Six
   Wearable Devices for Estimating Sleep, Heart Rate and Heart Rate
   Variability in Healthy Adults.* Sensors, 22(16), 6317.
   [doi:10.3390/s22166317](https://doi.org/10.3390/s22166317)
2. Stone, J. D., Rentz, L. E., Forse, J., et al. (2020). *Evaluations of
   Commercial Sleep Technologies for Objective Assessment of Sleep and
   Wakefulness.* Sleep, 43(Supplement_1), A81–A82.
3. Laurent, C., et al. (2021). *Validation of Sleep Tracking and Sleep Apnea
   Screening in the Withings ScanWatch against Polysomnography.* Journal of
   Sleep Research, 30(S1).
4. Chinoy, E. D., Cuellar, J. A., Huwa, K. E., et al. (2021). *Performance of
   seven consumer sleep-tracking devices compared with polysomnography.*
   SLEEP, 44(5), zsaa291. [doi:10.1093/sleep/zsaa291](https://doi.org/10.1093/sleep/zsaa291)
5. Pesonen, A. K., & Kuula, L. (2020). *The Validity of a New
   Accelerometer-Based Device in Measuring Sleep Architecture.* Sensors,
   20(3), 671.
6. Berryhill, S., Morton, P. R., et al. (2023). *Comparative Diagnostic
   Accuracy of Wearable Fitness Trackers in Detecting Sleep Stages.* Sleep
   Health, 9(2), 142–151.
7. Turner, T. H., et al. (2021). *Sleep Staging Accuracy of the Samsung
   Galaxy Watch: A Polysomnographic Validation Study.* Journal of Sleep
   Medicine, 18(2), 79–86.
8. de Zambotti, M., Goldstone, A., Claudatos, S., et al. (2018). *A
   validation study of Fitbit Charge 2™ compared with polysomnography in
   adults.* Chronobiology International, 35(4), 465–476.
9. Haghayegh, S., Khoshnevis, S., Smolensky, M. H., et al. (2020). *Accuracy
   of Wristband Fitbit Models in Assessing Sleep: Systematic Review and
   Meta-Analysis.* Journal of Medical Internet Research, 22(11), e23127.
10. Stucky, B., et al. (2021). *Validation of Fitbit Multi-Sensor Devices for
    Multi-State Sleep Architecture Assessment.* Sleep Medicine, 84, 324–331.
11. Apple Inc. (2023). *Estimating Sleep Stages with Apple Watch: Validation
    against Polysomnography.* Apple Health Technology White Paper.
12. Altini, M., & Kinnunen, H. (2021). *The Promise of Sleep: A Multi-Sensor
    Approach for Accurate Sleep Stage Identification Using the Oura Ring.*
    Sensors, 21(13), 4302. [doi:10.3390/s21134302](https://doi.org/10.3390/s21134302)
13. Arnal, P. J., Thorey, V., Debellemaniere, E., et al. (2020). *The Dreem
    Headband compared to polysomnography for electroencephalographic signal
    acquisition and sleep staging.* SLEEP, 43(11), zsaa097.
14. Rosenberg, R. S., & Van Hout, S. (2013). *The American Academy of Sleep
    Medicine Inter-scorer Reliability Program: Sleep Staging.* Journal of
    Clinical Sleep Medicine, 9(1), 81–87.
