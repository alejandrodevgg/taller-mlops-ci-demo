# taller-mlops-ci-demo

Taller MLOps pipeline — CI slice: `datos → entrena + gate → build + smoke + GHCR`.

![MLOps Pipeline](https://github.com/alejandrodevgg/taller-mlops-ci-demo/actions/workflows/mlops-ci.yml/badge.svg)

Three chained GitHub Actions jobs (`needs:`), SHA-pinned actions, a ROC-AUC
quality gate (`ROC_AUC_MIN=0.65`) before publish, and a double smoke test
(`/health` + `/predict`) inside the runner before the image is pushed to GHCR.

- Workflow: [`.github/workflows/mlops-ci.yml`](.github/workflows/mlops-ci.yml)
- Trigger: `workflow_dispatch` (Actions tab → *Run workflow*)
- Image published to: `ghcr.io/alejandrodevgg/flight-delay-api` (`:<sha>` and `:latest`)
- Raw data is NOT in git: `data-processing` regenerates `data/raw/flights.csv`
  deterministically (seed 42) via `scripts/make_flights_sample.py`.

Workshop companion repo — teaching narrative lives in the course material
(section 8 · CI).
