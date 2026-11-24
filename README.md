# aico-seeds

Platform-baseline seed data for [AICO](https://github.com/Aico-Systems/Umbrella).
Ships with every AICO install. Holds no customer data and no credentials.

## Profiles

- **`profiles/default/`** — minimum required platform data (provider configs
  without credentials, standard tool catalog, the `_default` org template).
  This is what a fresh partner install seeds when `SEED_PROFILE=default`.
  It also carries `flows/starter.json`, a conversation that reaches nobody, for
  the TEST org of a checkout without seeds-demo.
- **`SEED_PROFILE=none`** — nothing is seeded; for deployments that provision
  their data out-of-band.

The backend loads a profile on boot and applies it by `SEED_STRATEGY`
(`backend/src/seeds/README.md`). In host mode `just reseed` re-applies it.

## Logto starter (`logto/`)

The Logto seed data a host-mode checkout without seeds-demo uses: the TEST
organization and one fictional super admin (`dev`), whose password is
`"$AICO_DEV_ADMIN_PASSWORD"` (generated per machine into `.env.dev.local`).

## Sister repo

Demo/lab/test fixtures (private; TEST/DEMO/customer orgs, sample flows)
live in `aico-seeds-demo`.

## Env-var substitution

A whole-string `"$VAR_NAME"` in a profile's JSON is read from the env at seed
time; the rules are in `backend/src/seeds/README.md` ("Env-var substitution in
seed JSON"). Keep real credentials out of this repository.
