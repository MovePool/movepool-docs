---
description: Zero-Loss Savings Protocol on Movement Network
cover: .gitbook/assets/cover.png
coverY: 0
layout: landing
---

# MovePool

<figure><img src=".gitbook/assets/movepool-logo.png" alt="" width="200"><figcaption></figcaption></figure>

## The First Zero-Loss Savings Protocol on Movement

MovePool is a **gamified savings protocol** that turns your deposits into lottery tickets—without risking your principal.

{% hint style="success" %}
**Zero-Loss Guarantee**: Your deposit is always safe. Only yield is distributed as prizes.
{% endhint %}

### How It Works

1. **Deposit** MOVE tokens into the vault
2. **Get Tickets** proportional to your deposit (1 MOVE = 1 ticket)
3. **Win Prizes** funded by yield—not your principal
4. **Withdraw Anytime** with your full deposit intact

### Two Prize Pools

| Pool           | Draw Frequency | Prize Distribution |
| -------------- | -------------- | ------------------ |
| **Quick Draw** | Weekly         | 70% of yield       |
| **Jackpot**    | Monthly        | 30% of yield       |

### Quick Links

<table data-view="cards">
<thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead>
<tbody>
<tr><td><strong>🚀 Try the App</strong></td><td>Launch MovePool on Testnet</td><td><a href="https://movepool.vercel.app">https://movepool.vercel.app</a></td></tr>
<tr><td><strong>💧 Get Test MOVE</strong></td><td>Fund your wallet via faucet</td><td><a href="https://faucet.movementnetwork.xyz">https://faucet.movementnetwork.xyz</a></td></tr>
<tr><td><strong>📖 Read the Docs</strong></td><td>Quickstart guide</td><td><a href="getting-started/quickstart.md">getting-started/quickstart.md</a></td></tr>
</tbody>
</table>

---

### Built on Movement

<figure><img src=".gitbook/assets/movement-logo.png" alt="" width="150"><figcaption></figcaption></figure>

MovePool leverages the Movement Network's high throughput and low fees to deliver a fast, affordable savings experience.

---

### For Builders

Integrate MovePool into your app with our SDK:

```bash
npm install @movepool/sdk
```

```typescript
import { MovePoolClient } from "@movepool/sdk";

const client = new MovePoolClient({
  network: "testnet",
  contractAddress: "0x...",
});

// Get pool info
const pool = await client.getPoolInfo(0); // Quick Draw
console.log(`Prize: ${client.formatAmount(pool.accumulatedPrize)} MOVE`);
```

[Read SDK Documentation →](sdk/README.md)
