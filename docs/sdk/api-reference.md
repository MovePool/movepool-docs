# API Reference

Complete API documentation for `@movepool/sdk`.

## Class: MovePoolClient

### Constructor

```typescript
new MovePoolClient(config: MovePoolConfig)
```

**Parameters:**

| Name                     | Type                                 | Description                    |
| ------------------------ | ------------------------------------ | ------------------------------ |
| `config.network`         | `'mainnet' \| 'testnet' \| 'devnet'` | Network to connect             |
| `config.contractAddress` | `string`                             | Deployed contract address      |
| `config.rpcUrl`          | `string?`                            | Optional custom RPC URL        |
| `config.tokenDecimals`   | `number?`                            | Token decimals (default: 6)    |
| `config.tokenSymbol`     | `string?`                            | Token symbol (default: 'MOVE') |

---

## Read Methods

### getTotalAssets

```typescript
getTotalAssets(): Promise<number>
```

Returns total assets (MOVE) in the vault.

---

### getUserShares

```typescript
getUserShares(userAddress: string): Promise<number>
```

Returns user's share balance.

---

### getPoolInfo

```typescript
getPoolInfo(poolType: 0 | 1): Promise<PoolInfo>
```

**Pool Types:**

- `0` = Quick Draw (weekly)
- `1` = Jackpot (monthly)

**Returns:**

```typescript
interface PoolInfo {
  totalTickets: number;
  participantCount: number;
  accumulatedPrize: number;
  lastDrawTime: number;
}
```

---

### getAvailableYield

```typescript
getAvailableYield(poolType: 0 | 1): Promise<number>
```

Returns available prize for a pool.

---

### getTimeUntilDraw

```typescript
getTimeUntilDraw(poolType: 0 | 1): Promise<number>
```

Returns seconds until next draw.

---

### getUserPosition

```typescript
getUserPosition(userAddress: string, poolType: 0 | 1): Promise<UserPosition>
```

**Returns:**

```typescript
interface UserPosition {
  shares: number;
  tickets: number;
  prizesWon: number;
}
```

---

### getUserTickets

```typescript
getUserTickets(userAddress: string, poolType: 0 | 1): Promise<number>
```

Returns user's tickets in a pool.

---

### getUserPrizesWon

```typescript
getUserPrizesWon(userAddress: string): Promise<number>
```

Returns total prizes won by user.

---

## Transaction Builders

### createDepositPayload

```typescript
createDepositPayload(amount: number): TransactionPayload
```

Creates a deposit transaction payload.

**Example:**

```typescript
const payload = client.createDepositPayload(100_000_000); // 1 MOVE
await signAndSubmit(payload);
```

---

### createWithdrawPayload

```typescript
createWithdrawPayload(shares: number): TransactionPayload
```

Creates a withdraw transaction payload.

---

### createEnterDrawPayload

```typescript
createEnterDrawPayload(poolType: 0 | 1, depositAmount: number): TransactionPayload
```

Creates an enter draw transaction payload.

---

## Helper Methods

### formatAmount

```typescript
// Instance method
formatAmount(rawAmount: number, decimals?: number): string

// Static method
static formatAmount(rawAmount: number, tokenDecimals?: number, displayDecimals?: number): string
```

Formats raw amount to display string.

---

### parseAmount

```typescript
// Instance method
parseAmount(displayAmount: string): number

// Static method
static parseAmount(displayAmount: string, tokenDecimals?: number): number
```

Parses display amount to raw units.

---

### getTokenSymbol

```typescript
getTokenSymbol(): string
```

Returns configured token symbol.

---

### getContractAddress

```typescript
getContractAddress(): string
```

Returns contract address.
