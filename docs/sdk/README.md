# SDK Reference

The official SDK for integrating with MovePool.

## Installation

```bash
npm install @movepool/sdk
# or
yarn add @movepool/sdk
# or
pnpm add @movepool/sdk
```

## Quick Start

```typescript
import { MovePoolClient } from "@movepool/sdk";

const client = new MovePoolClient({
  network: "testnet",
  contractAddress: "0x88d3ef74bbce...",
  tokenDecimals: 8,
  tokenSymbol: "MOVE",
});

// Read pool info
const pool = await client.getPoolInfo(0);
console.log(`Prize: ${client.formatAmount(pool.accumulatedPrize)} MOVE`);

// Get user position
const position = await client.getUserPosition(userAddress, 0);
console.log(`Tickets: ${position.tickets}`);
```

## Configuration

| Option            | Type                                 | Required | Description                      |
| ----------------- | ------------------------------------ | -------- | -------------------------------- |
| `network`         | `'mainnet' \| 'testnet' \| 'devnet'` | ✅       | Network                          |
| `contractAddress` | `string`                             | ✅       | Contract address                 |
| `rpcUrl`          | `string`                             | ❌       | Custom RPC (auto-detected)       |
| `tokenDecimals`   | `number`                             | ❌       | Token decimals (default: 6)      |
| `tokenSymbol`     | `string`                             | ❌       | Display symbol (default: 'MOVE') |

## Read Methods

### `getTotalAssets()`

Returns total MOVE in the vault.

### `getUserShares(address)`

Returns user's share balance.

### `getPoolInfo(poolType)`

Returns pool stats (tickets, participants, prize, lastDraw).

### `getUserPosition(address, poolType)`

Returns user's complete position (shares, tickets, prizesWon).

### `getTimeUntilDraw(poolType)`

Returns seconds until next draw.

## Transaction Builders

### `createDepositPayload(amount)`

Creates deposit transaction payload.

### `createWithdrawPayload(shares)`

Creates withdraw transaction payload.

### `createEnterDrawPayload(poolType, amount)`

Creates enter draw transaction payload.

## Helpers

### `formatAmount(raw, decimals?)`

Formats raw amount to display string.

### `parseAmount(display)`

Parses display string to raw amount.

## Full Documentation

See the complete API reference: [API Reference →](api-reference.md)
