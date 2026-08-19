# aico-seeds

Platform-baseline seed data for [AICO](https://github.com/Aico-Systems/aicoyo).
Ships with every AICO install. Safe for public release.

## Profiles

- **`profiles/default/`** — minimum required platform data (provider configs
  without credentials, standard tool catalog, the `_default` org template).
  This is what a fresh partner install seeds when `SEED_PROFILE=default`.
- **`SEED_PROFILE=none`** — nothing is seeded; for deployments that provision
  their data out-of-band.

## Sister repo

Demo/lab/test fixtures (private; TEST/DEMO/customer orgs, sample flows)
live in `aico-seeds-demo`.

## Env-var substitution

Any JSON string that is exactly `"$VAR_NAME"` is resolved against
`process.env` at seed time (`backend/src/seeds/loaders/SeedLoader.ts`); an
unset variable seeds as `""` and is logged. Keep real credentials out of this
repo — add `secrets` blocks with placeholders and provide the values through
the deployment's secret source (Doppler, Vault, Kubernetes Secrets, the
partner's own `.env`).
