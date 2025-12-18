# Quickstart (Movement Testnet)

## 1) Open the app

Go to: https://movepool.vercel.app

## 2) Sign in (Privy)

- Click **Sign in**
- Use **Google** or **Email**
- An embedded Movement-compatible wallet will be created automatically

## 3) Fund your wallet (testnet MOVE)

1. Copy your wallet address from the dashboard header (click-to-copy is supported).
2. Open the faucet: https://faucet.movementnetwork.xyz/
3. Paste your address into the **MOVEMENT Address** field (top section) → click **GET MOVE**.

## 4) Deposit + get tickets

1. Go to **Deposit**
2. Enter an amount in MOVE
3. Confirm the transaction

Ticket math:

- **1 MOVE = 1 ticket** (MOVE has 8 decimals on testnet)

## 5) Enter pools

- **Quick Draw**: more frequent, 3 winners (70/20/10 split)
- **Jackpot**: larger prize, rolls over if not won

In the dashboard overview, click **Enter** for each pool.

## 6) Enable Auto-Enter (optional)

Turn on **Auto-enter** for Quick Draw / Jackpot to automatically re-enter the next round after a draw.

## 7) Refresh prize pools (demo helper)

Prize pools are funded by yield accrual. In testnet conditions, yield can be small.

Use **Update Prize Pools** to call `yield_strategy::accrue_yield` (note: accrual has a **1 hour minimum interval**).

## 8) Share your referral link (optional)

Use the Referral card to copy your referral link and invite others.
