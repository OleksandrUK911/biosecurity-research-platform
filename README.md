# Biosecurity Research Analytics Platform

Defensive, research-only analytics platform: ingests a biological sample,
runs quality control, extracts features, and produces an ML-based
classification / anomaly-detection report with a confidence score.

## Status
🔴 In planning — implementation not started yet.

## Stack
- **ML:** Python, scikit-learn (classification, Isolation Forest/Autoencoder)
- **Backend:** FastAPI, PostgreSQL
- **Frontend:** React, pipeline-status dashboard
- **Infra:** Docker, GitHub Actions

## How it works
```
Sample → ingestion → QC → feature extraction → ML analysis → report
```

## Important — scope and data
This project uses **public or synthetic data only** — no real lab, clinical,
or sensitive data. It is a **research/educational analytics tool**, not an
operational biosecurity system, and must not be used for designing or
optimizing pathogens or toxins.

## License
TBD
