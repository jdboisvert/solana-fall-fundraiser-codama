## Versions
anchor-cli 1.1.2 · solana-cli 3.1.10 · node 22.23.2 · @codama/cli 1.6.3

## TODO 3
Required: fundraiser, vault. Optional: contributorAccount, contributorAta,
tokenProgram, systemProgram. `contribute` seeds the fundraiser PDA on
`fundraiser.maker`, a field of the account being derived, so the finder
would need the account to find the account. `vault` inherits that: it is an
ATA of `authority = fundraiser` with `mint = fundraiser.mint_to_raise`, both
unreachable for the same reason. `initialize` seeds the fundraiser on the
`maker` account, which the caller has, so there it is optional.

## Bonus
Not attempted.

## One thing that surprised me
`anchor test` at the start reported everything successful even though it ran zero tests. Anchor runs [scripts] test through sh. sh has no globstar, so tests/**/*.ts collapsed to tests/*/*.ts and matched exactly one file which was tests/helpers/kit-adapter.ts, a helper with no tests in it.
