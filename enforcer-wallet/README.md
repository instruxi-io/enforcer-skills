# /enforcer-wallet

Custodial wallet management, transaction signing, and key backup/restore.

## When to use
- Building crypto wallet features (create, list, balance)
- Signing messages or transactions (EIP-191, EIP-712, EIP-7702, EIP-4337)
- Sending on-chain transactions
- Managing key backup and restore via Shamir secret sharing

## What it covers
- Custodial wallet creation and listing
- Balance queries
- Message signing (EIP-191 personal sign, EIP-712 typed data)
- Transaction signing and sending (EIP-7702, EIP-4337 account abstraction)
- Shamir-based key backup and restore

## Tips
- Wallets are custodial; private keys are managed server-side
- EIP-4337 endpoints require a bundler connection configured at the tenant level
- Shamir backup splits the key into shares; configure the threshold carefully
- Always verify the target chain ID before sending transactions
