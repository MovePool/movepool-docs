# Vercel Redeploy

Quick checklist for redeploying the MovePool Reference App on Vercel.

## When you MUST update Vercel env vars

### 1) After publishing contracts (new module address)

- `NEXT_PUBLIC_CONTRACT_ADDRESS` → update to the new module address

We redeploy contracts via resource accounts when struct storage layouts change.

### 2) If network endpoints change

- `NEXT_PUBLIC_MOVEMENT_RPC_URL`
- `MOVEMENT_INDEXER_URL` (server-only)

### 3) If your public domain changes

- `NEXT_PUBLIC_SITE_URL`

### 4) If token display changes

- `NEXT_PUBLIC_TOKEN_SYMBOL`
- `NEXT_PUBLIC_TOKEN_DECIMALS`

## Environment variables (template)

```bash
# Privy
NEXT_PUBLIC_PRIVY_APP_ID=

# Site
NEXT_PUBLIC_SITE_URL=https://movepool.vercel.app

# Movement
NEXT_PUBLIC_MOVEMENT_RPC_URL=https://seed-api.testnet.movementnetwork.xyz/v1
NEXT_PUBLIC_CONTRACT_ADDRESS=

# Movement Indexer (server-only)
MOVEMENT_INDEXER_URL=https://indexer.testnet.movementnetwork.xyz/v1/graphql

# Token
NEXT_PUBLIC_TOKEN_SYMBOL=MOVE
NEXT_PUBLIC_TOKEN_DECIMALS=8
```

Source of truth for local/dev: `movepool-app/apps/web/.env.example`.

## Redeploy flow

1. Publish contracts (only if needed) and capture the new module address.
2. Update Vercel env vars (Production + Preview recommended).
3. Trigger redeploy.
4. Smoke test:
   - Landing loads
   - Login works (Privy)
   - Dashboard loads (no fetch failures)
   - Deposit/withdraw works
   - Winners/leaderboard load (indexer-backed)
