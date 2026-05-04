# aico-seeds

Platform-baseline seed data for [AICO](https://github.com/Aico-Systems/aicoyo).
Ships with every AICO install. Safe for public release.

## Profiles

- **`profiles/default/`** — minimum required platform data (provider configs
  with `$VAR` placeholders, standard tool catalog, default-org template).
  This is what a fresh partner install seeds when `SEED_PROFILE=default`.
- **`profiles/none/`** — empty; for deployments that provision their seed
  data out-of-band (`SEED_PROFILE=none`).

## Sister repo

Demo/lab/test fixtures (private; TEST/DEMO/customer orgs, sample flows)
live in `aico-seeds-demo`.

## Env-var substitution

Any JSON string matching `"$VAR_NAME"` is resolved against `process.env`
at seed time. Keep real credentials out of this repo — use placeholders
and provide the values through the deployment's secret source (Doppler,
Vault, Kubernetes Secrets, partner's own `.env`).
