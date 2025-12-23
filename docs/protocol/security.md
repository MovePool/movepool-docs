# Security

MovePool is designed with security as a priority.

## Key Security Features

### 1. Zero-Loss Design

User principal is **never at risk**. Only yield is used for prizes.

```
User Deposit → Vault → Shares
          ↓
        Yield → Prize Pool → Winners
          ↓
User Withdrawal ← Vault ← Shares (principal intact)
```

### 2. Reserve-Backed Prizes

Prizes are paid from a **funded reserve**, not minted or borrowed:

- `fund_reserve(amount)` — Admin tops up reserve
- `get_reserve_balance()` — Verify available funds
- Draws fail if reserve is insufficient

### 3. Admin Controls

Critical functions are admin-gated:

| Function            | Protection                     |
| ------------------- | ------------------------------ |
| `execute_draw`      | Interval check + authorization |
| `update_*_interval` | Admin-only                     |
| `pause/unpause`     | Admin-only                     |
| `fund_reserve`      | Admin-only                     |

### 4. Pause Mechanism

In emergencies, the admin can pause the protocol:

- Deposits blocked
- Withdrawals blocked
- Draws suspended

This prevents exploitation during vulnerability disclosure.

### 5. Price-Per-Share Invariant

PPS can only **increase or stay flat**, never decrease:

```
new_pps = max(old_pps, calculated_pps)
```

This prevents share dilution attacks.

## Audit Status

{% hint style="warning" %}
**Not Audited**: MovePool is currently unaudited testnet software. Use at your own risk.
{% endhint %}

## Bug Reports

Found a vulnerability? Please report responsibly:

1. **Do not** disclose publicly
2. Contact the team directly
3. Allow time for a fix before disclosure

## Open Source

All contracts are open source:

- [GitHub Repository](https://github.com/MovePool)
- [Contract Source](https://github.com/MovePool/movepool-app/tree/main/packages/protocol)
