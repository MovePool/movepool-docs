# Protocol Overview

MovePool is a zero-loss savings protocol built with six core Move modules working together seamlessly.

## Architecture

The protocol follows a modular design where each component has a single responsibility:

| Module            | Purpose                                             |
| ----------------- | --------------------------------------------------- |
| **Vault**         | Manages deposits, withdrawals, and share accounting |
| **Lottery**       | Handles ticket allocation and prize draw execution  |
| **YieldStrategy** | Simulates yield accrual and funds prize pools       |
| **Arcade**        | Tracks XP, levels, streaks, and badge unlocks       |
| **Referrals**     | Manages on-chain referrer binding and bonus rewards |
| **Admin**         | Protocol configuration and access control           |

### Data Flow

1. **User deposits MOVE** → Vault mints shares
2. **Vault credits yield** → YieldStrategy allocates to prize pools
3. **User enters draw** → Lottery records tickets (weighted by deposit)
4. **Draw executes (VRF)** → Winner receives prize from reserve
5. **User withdraws** → Vault burns shares, returns MOVE

---

## Modules

### Vault (`vault.move`)

The vault holds all user deposits and manages share-based accounting.

**Key Functions:**

| Function                   | Description                  |
| -------------------------- | ---------------------------- |
| `deposit(amount)`          | Deposit MOVE, receive shares |
| `withdraw(shares)`         | Burn shares, receive MOVE    |
| `get_user_shares(address)` | Query user's share balance   |
| `get_price_per_share()`    | Current share price (PPS)    |

**Share Math:**

```
shares = deposit_amount × PRECISION ÷ price_per_share
```

---

### Lottery (`lottery.move`)

Manages prize pools and draw execution using verifiable randomness.

**Pool Types:**

| Pool       | ID  | Draw Interval | Yield Allocation |
| ---------- | --- | ------------- | ---------------- |
| Quick Draw | 0   | 7 days        | 70%              |
| Jackpot    | 1   | 30 days       | 30%              |

**Key Functions:**

| Function                               | Description                         |
| -------------------------------------- | ----------------------------------- |
| `enter_draw(pool_type, amount)`        | Enter a draw with tickets           |
| `execute_draw(pool_type)`              | Run the draw, select winner via VRF |
| `get_user_tickets(address, pool_type)` | Query ticket count                  |

---

### Yield Strategy (`yield_strategy.move`)

Manages yield simulation and prize reserve funding.

**Key Concepts:**

- **Reserve**: Holds real tokens backing all prize payouts
- **Accrual**: Calculates yield based on simulated APY (12%)
- **Backed Prizes**: Payouts limited to actual reserve balance

**Key Functions:**

| Function                        | Description                           |
| ------------------------------- | ------------------------------------- |
| `accrue_yield()`                | Calculate and allocate yield to pools |
| `fund_reserve(amount)`          | Top up prize reserve                  |
| `get_reserve_balance()`         | Check available funds                 |
| `take_prize(pool_type, amount)` | Extract coins for winner payout       |

---

### Arcade (`arcade.move`)

Gamification layer for user engagement and retention.

**Features:**

- **XP**: Earned on deposits, draws, and wins
- **Levels**: Calculated from cumulative XP (1-100+)
- **Streaks**: Daily participation multipliers
- **Badges**: Permanent on-chain achievements (stored as bitset)

---

### Referrals (`referrals.move`)

On-chain referral tracking and bonus distribution.

**Features:**

- One-time referrer binding per user
- +5 bonus tickets on first deposit
- Transparent on-chain tracking

---

### Admin (`admin.move`)

Protocol governance and configuration management.

**Configurable Parameters:**

| Parameter      | Description                     |
| -------------- | ------------------------------- |
| Draw intervals | Quick Draw (7d) / Jackpot (30d) |
| Yield split    | 70% / 30% allocation            |
| APY rate       | Simulated yield percentage      |
| Pause state    | Emergency stop capability       |

---

## Security Model

1. **Admin-only functions** require signer verification against `@movepool_admin`
2. **Pause capability** for emergency protocol stops
3. **Reserve-backed prizes** — cannot pay out more than funded
4. **No dilution** — PPS only increases or stays flat
5. **VRF randomness** — provably fair winner selection
