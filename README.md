# TipJar

A personal tip jar deployed as a Soroban smart contract. Supporters send XLM with an optional message. The creator sees every tip in a live feed and withdraws accumulated funds whenever they like. Each jar is a standalone contract — one per creator.

## Live Links

| | |
|---|---|
| **Frontend** | `https://tipjar-stellar.vercel.app` |
| **Contract** | `https://stellar.expert/explorer/testnet/contract/CDDVZTKGRH7UHWOWRABRYYGCLTZS63I7OZZXR75UAOTSJX4ZE7SXP2HV` |

## How It Works

1. **Deploy** the contract — you get your own unique contract address
2. **Setup** — owner calls `setup()` with name and bio
3. **Share** the URL — supporters open it and send XLM tips with messages
4. **Withdraw** — owner calls `withdraw()` anytime to collect all accumulated tips

## Why This Project Matters

This project turns a familiar real-world workflow into a verifiable on-chain primitive on Stellar: transparent state transitions, user-authenticated actions, and deterministic outcomes.

## Architecture

- **Smart Contract Layer**: Soroban contract enforces business rules, authorization, and state transitions.
- **Client Layer**: React + Vite frontend handles wallet UX, transaction composition, and real-time status views.
- **Wallet/Auth Layer**: Freighter signs every state-changing action so operations are attributable and non-repudiable.
- **Infra Layer**: Stellar Testnet + Soroban RPC for execution; Vercel for frontend hosting.
## Contract Functions

```rust
setup(owner, name, bio)
tip(tipper, amount: i128, message, xlm_token)
withdraw(owner, xlm_token)         // owner only, empties balance
get_profile() -> CreatorProfile
get_tips() -> Vec<Tip>             // last 50 tips, newest first
```

## Stack

| Layer | Tech |
|---|---|
| Contract | Rust + Soroban SDK v22 |
| Network | Stellar Testnet |
| Frontend | React 18 + Vite |
| Wallet | Freighter v1.7.1 |
| Hosting | Vercel |

## Run Locally

```bash
chmod +x scripts/deploy.sh && ./scripts/deploy.sh
cd frontend && npm install && npm run dev
```


