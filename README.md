[README.md](https://github.com/user-attachments/files/25606780/README.md)
# ChainScore
### On-Chain Trading Signal Intelligence — Powered by Avalanche

> *"No black boxes. No Telegram gurus. Just math on-chain."*

🔴 **Live Demo:** [batbug648.github.io/chainscore](https://batbug648.github.io/chainscore)  
📄 **Contract (Fuji):** `0xC12795665710bCC9E99304a4464Febe2265b7E1d`  
⛓️ **Chain:** Avalanche C-Chain  

---

## What is ChainScore?

ChainScore is an on-chain trading signal platform built on Avalanche. It detects bullish candlestick patterns and volume anomalies across S&P 500 stocks, NASDAQ 100 stocks, and top crypto pairs — then publishes the highest-confidence setups directly to the Avalanche C-Chain, ranked by a scientific scoring system.

Every signal is timestamped on-chain at publish time. Outcomes are verified 48 hours later using live price data. The accuracy record is immutable and publicly readable by anyone.

Users pay **0.1 AVAX per day** to access the full signal feed. That's it. No subscriptions to cancel, no middlemen, no black boxes.

---

## Why Avalanche?

ChainScore was designed from the ground up to generate **daily recurring AVAX burn** through consistent on-chain activity.

### How burn is generated:

| Action | Frequency | Transactions |
|--------|-----------|-------------|
| Signal published | Every 30 min during market hours | ~16/day |
| Signal resolved | 48hrs after each signal | ~16/day |
| User subscribes | Daily per active user | 1 per user/day |
| Accuracy updated | After each resolution | ~16/day |

With 100 active users that's **3,000+ transactions per month** — all burning AVAX gas on C-Chain.

The daily access model was chosen specifically because it maximizes transaction frequency compared to monthly subscriptions. Every day a user wants access, they transact. Every transaction burns gas. The more useful ChainScore becomes, the more burn it generates.

---

## How It Works

```
Your Scanner (local)
      ↓
Detects bullish patterns + volume spikes
      ↓
Scores each setup (1-17 points)
      ↓
Score 7+ → Publisher pushes signal on-chain
      ↓
Signal timestamped to Avalanche C-Chain
      ↓
48 hours later → outcome verified by live price
      ↓
Accuracy score updates on-chain automatically
      ↓
Subscribers read signals from dashboard
```

---

## The Scoring System

Every signal is ranked using a multi-factor scoring engine:

| Factor | Points |
|--------|--------|
| Three White Soldiers / Morning Star | +5 |
| Bullish Engulfing / Piercing Pattern | +4 |
| Bullish Marubozu / Tweezer Bottoms | +3 |
| Bullish Harami / Hammer | +2 |
| Volume Spike (4x average) | +3 |
| Volume Spike (2x average) | +2 |
| Uptrend context (EMA 20/50) | +2 |
| Multi-pattern convergence | +2 |

Signals scoring 7+ are published on-chain. The higher the score, the stronger the setup. Maximum possible score: **17**.

Confidence labels:
- **10+** → Exceptional
- **8-9** → Very Strong
- **6-7** → Strong
- **4-5** → Moderate
- **1-3** → Weak

---

## Signal Universe

**Stocks (price filtered $5–$50):**
- S&P 500 components
- NASDAQ 100 components
- Scanned Monday–Friday 9:30am–4:00pm EST

**Crypto (no price filter, 24/7):**
- BTC, ETH, SOL, AVAX, XRP, ADA, LINK, DOT, ETC, and more
- Scanned continuously around the clock

**After hours:**
- Cached last market close signals served to stock subscribers
- Live crypto scanning continues 24/7
- Users always have relevant signals regardless of time zone

---

## Smart Contract

**ChainScore.sol** is deployed on Avalanche C-Chain (Fuji testnet).

Key functions:

```solidity
// Users pay 0.1 AVAX per day
function subscribe() external payable

// Publisher pushes high-score signals on-chain
function publishSignal(ticker, pattern, score, confidence, trend, price) external

// Outcomes recorded 48hrs after publish
function resolveSignal(signalId, wasCorrect) external

// Anyone can read accuracy — no subscription needed
function getAccuracy() public view returns (correct, total, percentage)

// Free preview of last 3 signals — drives subscriptions
function getPreviewSignals() external view

// Subscribers read full feed
function getLatestSignals(count) external view
```

The contract is fully verified on Snowtrace. Source code is publicly readable.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Pattern Detection | Python + yfinance |
| On-Chain Publisher | Python + web3.py |
| Smart Contract | Solidity 0.8.20 |
| Blockchain | Avalanche C-Chain |
| Frontend | HTML/CSS/JS + ethers.js |
| Hosting | GitHub Pages |
| Price Data | Yahoo Finance (free, no API key) |
| Market Hours | EST timezone detection |

---

## Dashboard Features

- **Connect MetaMask** — auto-switches to Avalanche C-Chain
- **Live Top 5 signals** — pulled directly from contract
- **Free preview** — last 3 signals visible without subscription
- **Locked placeholders** — drives conversion to paid access
- **Accuracy ring** — animated on-chain win rate
- **Market status** — live open/closed indicator
- **One-click subscribe** — 0.1 AVAX, instant access

---

## Roadmap

**Phase 1 — Fuji Testnet** ✅
- Smart contract deployed and verified
- Pattern scanner operational
- Publisher script live
- Dashboard hosted on GitHub Pages

**Phase 2 — Mainnet Launch**
- Deploy ChainScore.sol to Avalanche mainnet
- Publisher switches to mainnet RPC
- Custom domain (chainscore.io)

**Phase 3 — Behavior Engine**
- Track which patterns each user wins with
- Personalized signal weighting
- "Your Edge Today" dashboard widget

**Phase 4 — Signal Marketplace**
- Allow third-party signal providers to publish
- On-chain reputation scores for each provider
- Subscribers choose which providers to follow

---

## Why This Matters

Most trading signal services are a black box. Some person on Telegram says "buy this" and you have no idea if they're right 60% of the time or 20%. There's no accountability, no transparency, no verifiable track record.

ChainScore fixes that. Every signal is published on-chain with a timestamp before the outcome is known. Every resolution is recorded immutably. The accuracy score cannot be edited, deleted, or manipulated. Anyone can audit the full history at any time.

For traders learning technical analysis, ChainScore is also an educational tool — every signal comes with the pattern name, the score breakdown, and the outcome. Over time users can see which patterns work best in which market conditions, building real trading intuition backed by on-chain data.

---

## Built By

Brian Gregory — Solo developer  
Built for Retro9000 — Avalanche Ecosystem Grant Program

---

*ChainScore is experimental software. Trading signals are not financial advice. Past accuracy does not guarantee future results. Always do your own research.*
