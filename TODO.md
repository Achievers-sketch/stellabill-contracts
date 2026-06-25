# TODO

## feat/merchant-kyc-attestation

- [ ] Step 1: Update `contracts/subscription_vault/src/types.rs`
  - Append new `DataKey` variants for `KycRequired` and `MerchantKyc(Address)`.
  - Add `MerchantKyc` struct.
  - Add `MerchantKycAttachedEvent` and `MerchantKycRevokedEvent`.
- [ ] Step 2: Update `contracts/subscription_vault/src/admin.rs`
  - Add admin-only `do_set_kyc_required` and `get_kyc_required` helpers.
- [ ] Step 3: Update `contracts/subscription_vault/src/merchant.rs`
  - Implement `attach_merchant_kyc` + `revoke_merchant_kyc`.
  - Add helper to check active KYC.
  - Gate `withdraw_merchant_funds_for_token` with global `kyc_required`.
- [ ] Step 4: Update `contracts/subscription_vault/src/lib.rs`
  - Add public entrypoints for attaching/revoking KYC and setting global flag.
- [ ] Step 5: Update/add tests in `contracts/subscription_vault/src/test.rs`
  - KYC required off: withdraw unchanged.
  - KYC required on: missing KYC => `Error::Forbidden`.
  - attach -> success
  - revoke -> blocked
  - double-attach rejected
- [ ] Step 6: Run `cargo test --all` and address failures.
- [ ] Step 7: Document in `docs/merchant_config.md` and/or `docs/withdrawals.md`.
- [ ] Step 8: Ensure coverage >= 95% (or add tests until threshold met).

