# Lottery Pools

MovePool has two prize pools with different draw frequencies.

---

## Quick Draw (Weekly)

| Property             | Value                        |
| -------------------- | ---------------------------- |
| **Draw Frequency**   | Every 7 days                 |
| **Yield Allocation** | 70% of total yield           |
| **Winners per Draw** | 3                            |
| **Prize Split**      | 1st: 70%, 2nd: 20%, 3rd: 10% |

Best for: Users who want frequent winning opportunities.

---

## Jackpot (Monthly)

| Property             | Value                      |
| -------------------- | -------------------------- |
| **Draw Frequency**   | Every 30 days              |
| **Yield Allocation** | 30% of total yield         |
| **Winners per Draw** | 1                          |
| **Rollover**         | Yes, if conditions not met |

Best for: Users chasing bigger prizes.

{% hint style="warning" %}
**Rollover:** If the jackpot threshold isn't met, the prize rolls over to the next month, growing even larger!
{% endhint %}

---

## How Winners Are Selected

1. **VRF Randomness** — Uses on-chain verifiable random function
2. **Weighted by Tickets** — More tickets = higher chance to win
3. **Provably Fair** — Anyone can verify the draw on-chain

---

## Ticket Calculation

```
1 MOVE deposited = 1 ticket
```

Tickets are calculated at draw time based on your deposited amount.

---

## Prize Distribution

When you win:

1. Prize is transferred directly to your wallet
2. Confetti celebration on the app 🎉
3. You appear in the Winners feed
4. XP bonus for winning!

---

[← Deposit & Withdraw](deposit-withdraw.md) | [Gamification →](gamification.md)
