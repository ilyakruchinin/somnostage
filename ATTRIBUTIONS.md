# Data sources & attributions

SomnoStage was developed and evaluated using public research datasets. All
sources are distributed under attribution-only or public-domain licenses —
no dataset is non-commercial, share-alike, or access-gated. Per the
[licensing requirements](NOTICE), the model ships no dataset content; only
the attribution below.

Grouped by the role each source played. No dataset sizes or per-source
statistics are listed here by design; the corpus description in
[README.md](README.md#training-data) gives the aggregate picture.

## Core training corpora

| Dataset | License | Required citation |
|---|---|---|
| PhysioNet/Computing in Cardiology Challenge 2018 ("You Snooze, You Win") | ODC-By 1.0 | Ghassemi MM, Moody BE, Lehman L, Song C, Li Q, Sun H, Mark RG, Westover MB, Clifford GD. *You snooze, you win: the PhysioNet/Computing in Cardiology Challenge 2018.* Computing in Cardiology (CinC) 2018;45:1–4. [doi:10.22489/CinC.2018.049](https://doi.org/10.22489/CinC.2018.049) — dataset: [doi:10.13026/1q9b-ge17](https://doi.org/10.13026/1q9b-ge17) |
| The Bitbrain Open Access Sleep (BOAS) dataset — OpenNeuro ds005555 (snapshot 1.1.3) | CC0 | OpenNeuro dataset DOI: [10.18112/openneuro.ds005555.v1.1.3](https://doi.org/10.18112/openneuro.ds005555.v1.1.3) |

## Development & auxiliary cohorts

| Dataset | License | Required citation |
|---|---|---|
| BIDSleep — A Multi-Night Instantaneous Heart Rate and Accelerometry Dataset with EEG Sleep Stage Labels | ODC-By 1.0 | Song, T.-A. (2026). PhysioNet. [doi:10.13026/a0sy-7t69](https://doi.org/10.13026/a0sy-7t69) — and Song, T.-A. et al. (2025). *AI-driven sleep staging using instantaneous heart rate and accelerometry: Insights from an Apple Watch study.* IEEE Trans. Biomed. Eng. [doi:10.1109/TBME.2025.3612158](https://doi.org/10.1109/TBME.2025.3612158) |
| Sleep-Accel — Motion and heart rate from a wrist-worn wearable and labeled sleep from polysomnography | ODC-By 1.0 | Walch, O. (2019). PhysioNet. [doi:10.13026/hmhs-py35](https://doi.org/10.13026/hmhs-py35) — and Walch O, Huang Y, Forger D, Goldstein C. *Sleep stage prediction with raw acceleration and photoplethysmography heart rate data derived from a consumer wearable device.* Sleep 2019. |
| Haaglanden Medisch Centrum sleep staging database | CC BY 4.0 | Alvarez-Estevez, D. & Rijsman, R. (2022). PhysioNet. [doi:10.13026/t79q-fr32](https://doi.org/10.13026/t79q-fr32) — and Alvarez-Estevez D, Rijsman RM (2021). *Inter-database validation of a deep learning approach for automatic sleep scoring.* PLoS ONE 16(8):e0256111. [doi:10.1371/journal.pone.0256111](https://doi.org/10.1371/journal.pone.0256111) |
| Respiratory and Pulse Oximetry Waveforms from Healthy Adults During Simulated Apnoea Events | CC BY 4.0 | Hill, J., Guy, E. F. S., Clifton, J. A., Pretty, C., & Chase, J. G. (2026). PhysioNet. [doi:10.13026/s45r-k263](https://doi.org/10.13026/s45r-k263) |
| APNEA HRV+SPO2 Dataset (HuGCDN2014-OXI) | CC BY 4.0 | Juliá-Serdá, G., Navarro-Esteva, J., & Ravelo-García, A. G. (2023). Mendeley Data. [doi:10.17632/cdxs63gdzc.1](https://doi.org/10.17632/cdxs63gdzc.1) |

## Evaluation-only cohorts

These datasets were used to evaluate the model and were **not** used for
training.

| Dataset | License | Required citation |
|---|---|---|
| CAP Sleep Database | ODC-By 1.0 | Terzano MG, Parrino L, Sherieri A, et al. *Atlas, rules, and recording techniques for the scoring of cyclic alternating pattern (CAP) in human sleep.* Sleep Med 2001;2(6):537–553. — dataset: [doi:10.13026/C2VC79](https://doi.org/10.13026/C2VC79) |
| St. Vincent's University Hospital / University College Dublin Sleep Apnea Database (UCDDB) | ODC-By 1.0 | Dataset: [doi:10.13026/C26C7D](https://doi.org/10.13026/C26C7D) |
| Aalborg University Wearable Sleep Study (AAUWSS) | CC BY 4.0 | Dataset: [doi:10.5281/zenodo.16919071](https://doi.org/10.5281/zenodo.16919071) — and, per the dataset record, Djanian S, Nielsen TD, Nielsen SH, Bruun A. *Towards real-time sleep stage classification: A deep learning approach leveraging PPG and ECG.* Physiol. Meas. 2026. [doi:10.1088/1361-6579/ae5458](https://doi.org/10.1088/1361-6579/ae5458) |
| MIT-BIH Polysomnographic Database (SLPDB) | ODC-By 1.0 | Ichimaru Y, Moody GB. *Development of the polysomnographic database on CD-ROM.* Psychiatry Clin Neurosci 1999;53:175–177. — dataset: [doi:10.13026/C23K5S](https://doi.org/10.13026/C23K5S) |

## PhysioNet

PhysioNet-hosted datasets additionally request the standard PhysioNet
citation:

> Pollard, T., Moody, B. E., Lehman, L., Gow, B., Fernandes, C., Xie, C.,
> Johnson, A., Mark, R. G., & Heldt, T. (2026). PhysioNet as a global
> platform for biomedical research. *Nature Health.*
> [doi:10.1038/s44360-026-00096-z](https://doi.org/10.1038/s44360-026-00096-z)
