# Protocol Overview

## Core idea

MovePool is built around a simple invariant:

> **Principal is never paid out as prizes.** Prizes come from yield.

Deposits are tracked via a share-based vault (ERC-4626-style accounting), where the **price-per-share (PPS)** only increases when yield is credited.

## Pools

MovePool maintains **two isolated pools**:

- **Quick Draw** (pool type `0`): weekly by default, **3 winners** (70% / 20% / 10%)
- **Jackpot** (pool type `1`): monthly by default, **1 winner**, rolls over if conditions aren’t met

Intervals are admin-configurable.

## Tickets

- **1 MOVE = 1 ticket**
- MOVE on Movement testnet is represented as `0x1::aptos_coin::AptosCoin` and branded as **MOVE** with **8 decimals**.

## Yield strategy (hackathon/testnet)

Yield is simulated for testnet using a mock strategy:

- Default **APY**: 12%
- Yield split: **70% → Quick Draw**, **30% → Jackpot**
- Accrual rate is time-based, with a minimum accrual interval of **1 hour**

In production, this module would be replaced by real integrations.

## Key modules

Located in: `movepool-app/packages/protocol/sources/`

- `admin.move`: protocol config, intervals, APY, pause, admin transfer
- `vault.move`: deposits/withdrawals, shares, PPS math
- `yield_strategy.move`: mock yield accrual + allocation
- `lottery.move`: pool state, tickets, draw execution (VRF), winner selection, prize crediting
- `arcade.move`: XP/levels/streaks/badges (on-chain progression)
- `referrals.move`: on-chain referral binding + bonus tickets

## Event indexing

The web app fetches module events primarily through the Movement **GraphQL indexer** (server-only `MOVEMENT_INDEXER_URL`) and falls back to RPC event endpoints.
