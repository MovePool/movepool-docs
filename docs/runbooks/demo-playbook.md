# Demo Playbook (Hackathon)

This playbook is optimized for a short live demo or a 2–3 minute screen recording.

## Pre-demo checklist

- App is live: https://movepool.vercel.app
- Your demo wallet is funded (testnet MOVE)
- You know which wallet is **admin** (only admin can change protocol parameters)

## Recommended demo flow (3–5 minutes)

1. **Hook**
   - “What if you could play the lottery and never lose your money?”

2. **Sign in with Google (Privy)**
   - Highlight embedded wallet auto-creation.

3. **Fund wallet (faucet)**
   - Copy address → faucet → claim MOVE.

4. **Deposit MOVE**
   - Explain: deposits mint shares; principal remains withdrawable.

5. **Enter Quick Draw + Jackpot**
   - Highlight: 1 MOVE = 1 ticket.

6. **Turn on Auto-Enter**
   - Show it persists on-chain.

7. **Show engagement layer**
   - Stats page (levels / targets)
   - Leaderboard
   - Winners page
   - Referral link (copy + share)

## Prize pool visibility (important)

Prize pools come from yield accrual. For testnet demos:

- Use **Update Prize Pools** to call `yield_strategy::accrue_yield`.
- Accrual has a **1-hour minimum interval**, so you may need to wait before it changes again.

## Optional: “fast demo” draw intervals (admin-only)

By default, intervals are 7 days (Quick Draw) and 30 days (Jackpot). For a live demo, it’s common to temporarily shorten them.

Admin can update intervals via `movepool::admin` (e.g., set Quick Draw to 60 seconds).

> Note: draw execution is admin/keeper-only and should be automated by a keeper in production.
