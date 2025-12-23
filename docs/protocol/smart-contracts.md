# Smart Contracts

MovePool is deployed on Movement Testnet.

## Contract Address

```
0x88d3ef74bbce0929174ae0d8f1dfa4c8e17d0cda1b3fe5c839d241fc8f774481
```

## Modules

### vault.move

Handles deposits, withdrawals, and share accounting.

| Function                    | Type  | Description              |
| --------------------------- | ----- | ------------------------ |
| `deposit(amount)`           | entry | Deposit MOVE tokens      |
| `withdraw(shares)`          | entry | Withdraw shares for MOVE |
| `get_total_assets()`        | view  | Total MOVE in vault      |
| `get_user_shares(addr)`     | view  | User's share balance     |
| `get_price_per_share()`     | view  | Current PPS (6 decimals) |
| `get_user_prizes_won(addr)` | view  | Total prizes won         |

### lottery.move

Manages prize pools and draws.

| Function                        | Type  | Description            |
| ------------------------------- | ----- | ---------------------- |
| `enter_draw(pool, amount)`      | entry | Deposit + get tickets  |
| `execute_draw(pool)`            | entry | Run draw (keeper only) |
| `set_auto_enter(pool, enabled)` | entry | Toggle auto-enter      |
| `get_pool_info(pool)`           | view  | Pool stats             |
| `get_user_tickets(addr, pool)`  | view  | Ticket count           |
| `get_time_until_draw(pool)`     | view  | Seconds until draw     |

### yield_strategy.move

Yield generation and reserve management.

| Function                    | Type  | Description           |
| --------------------------- | ----- | --------------------- |
| `accrue_yield()`            | entry | Accrue yield to pools |
| `fund_reserve(amount)`      | entry | Top up reserve        |
| `get_reserve_balance()`     | view  | Available reserve     |
| `get_available_prize(pool)` | view  | Prize for pool        |

### admin.move

Protocol configuration.

| Function                        | Type  | Description      |
| ------------------------------- | ----- | ---------------- |
| `update_quick_draw_interval(s)` | entry | Set QD interval  |
| `update_jackpot_interval(s)`    | entry | Set JP interval  |
| `pause()`                       | entry | Pause protocol   |
| `unpause()`                     | entry | Unpause protocol |
| `get_admin()`                   | view  | Admin address    |

## Verifying on Explorer

View the contract on Movement Explorer:

[Movement Explorer →](https://explorer.movementnetwork.xyz/account/0x88d3ef74bbce0929174ae0d8f1dfa4c8e17d0cda1b3fe5c839d241fc8f774481?network=testnet)
