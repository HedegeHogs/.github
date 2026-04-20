# HedgeHog Protocol

**Automated DeFi Position Management Across Multiple Protocols**

HedgeHog is a production-ready DeFi automation platform that enables users to create complex, automated position management strategies across multiple protocols with self-custody and gas optimization.

---

## What is HedgeHog?

## 🧠 Product mental model

HedgeHogs is an aggregator of LP pools + lending markets with an automation layer on top. Users freely pick any pool or lending opportunity; automation (auto-harvest / auto-compound / auto-rebalance / auto-repay / auto-collateralize) is an opt-in layer applied AFTER the user opens a position. Not a catalog of canned strategies. References: Pendle (markets-first), Vaults.fyi (yield aggregator), DeBank (discovery). Not Yearn/Summers.fi (strategy-first).

HedgeHog allows you to:
- 🤖 **Automate DeFi strategies** - Set-and-forget position management across Aave, Uniswap V3, Curve, and more
- 🔐 **Maintain full control** - Your funds stay in your personal proxy contract, not the protocol
- ⚡ **Save on gas** - 67-85% reduction in approval costs through JIT (Just-In-Time) approvals
- 🌐 **Go cross-protocol** - Execute complex strategies spanning multiple DeFi protocols atomically
- 📊 **Track everything** - Comprehensive position and yield tracking across all your DeFi activities

---

## Architecture

HedgeHog uses a novel **"Sickle Pattern"** architecture:

```
User/Bot → Strategy → HH Proxy (your personal contract) → Connectors → DeFi Protocols
```

### Key Components

- **HH Proxy**: Your personal smart contract that owns ALL your DeFi positions (aTokens, LP NFTs, debt)
- **Strategies**: Orchestrate multi-step operations (e.g., borrow from Aave + provide liquidity to Uniswap)
- **Connectors**: Stateless protocol adapters that execute operations via delegatecall
- **Bot Network**: Decentralized automation executing strategies on your behalf

---

## Supported Protocols

### Lending
- **Aave V3** - Supply, borrow, collateral management
- **Morpho Blue** - Optimized lending markets
- **Compound V3** - Comet markets

### Liquidity Provision
- **Uniswap V3** - Concentrated liquidity positions
- **Curve** - Stable swap pools
- **Balancer V2** - Weighted pools
- **Aerodrome** - Base chain DEX

### Yield Aggregators
- **Yearn V3** - Automated vault strategies

### Swap Aggregation
- **KyberSwap** - Best execution across 70+ DEXs

---

## Key Innovations

### 1. Just-In-Time Approvals
Instead of approving every protocol upfront ($100s in gas), users approve their proxy once. The proxy manages all protocol approvals using the approve/call/reset pattern.

### 2. Proxy-Centric Ownership
Your HH Proxy owns all positions, enabling universal automation even for protocols that don't support delegation (like Uniswap V3 NFTs).

### 3. Stateless Connectors
Protocol adapters have NO state, NO immutables, NO events. They're pure logic contracts that work with any protocol version via parameterized addresses.

### 4. Dual-Context Fees
- User direct execution: 0.5% fee
- Bot automation: 0.1% fee
- Volume discounts for high-activity users

### 5. Cross-Protocol Atomicity
Execute complex strategies spanning multiple protocols in a single transaction. If any step fails, everything reverts.


## Community & Support

- **Twitter**: [@HedgehogDeFi](https://twitter.com/HedgehogDeFi)
- **Discord**: [Join our community](https://discord.gg/hedgehog)
- **Email**: team@hedgehogs.app


**Built with ❤️ by the HedgeHog team**
