# OmniBus — Multi-Regime RSI Rotation Strategy

## Skill Name
OmniBus

## Strategy Type
Trend / Mean-Reversion Hybrid (regime-adaptive)

## Applicable Market
- Futures (leveraged)
- Cross-market: BTCUSDT + ETHUSDT (simultaneous execution)
- Specific market condition (bull / bear / choppy detection)

## Core Logic
OmniBus is a market-state detection bot that classifies the market into
one of three regimes — bull, bear, or choppy/fear — and applies a
regime-appropriate rule to BTCUSDT and ETHUSDT simultaneously, removing
discretionary/emotional entries.

**Indicator:** RSI (14-period)
**Timeframe:** 4H candles

**Signal rules:**
- SELL entry: RSI > 70 on the 4H chart (overbought — uptrend exhausted,
  reversal expected)
- BUY entry: RSI < 30 on the 4H chart AND a "W" double-bottom candle
  pattern confirms downtrend exhaustion
- NO TRADE / stand aside: RSI ≈ 50 on the 4H chart (choppy, no
  directional edge) — wait for a cleaner entry

## Key Parameters
| Parameter | Value |
|---|---|
| Timeframe | 4H |
| RSI period | 14 |
| RSI overbought threshold | 70 |
| RSI oversold threshold | 30 |
| Neutral/choppy zone | ~50 (no entry) |
| Leverage | 5–10x |
| Stop loss | 19% of capital entry amount |
| Take profit | 50–65% gain on capital entry amount |
| Pairs traded | BTCUSDT, ETHUSDT (concurrent) |

## Risk Notice
- **Max risk per position:** capped at 19% of the entry capital via stop loss
- **Invalidation condition:** if price breaches the stop-loss level on the
  4H close, the trade thesis (overbought/oversold exhaustion) is
  considered invalid and the position is closed — no averaging down
- **Leverage risk:** 5–10x leverage amplifies both gains and the 19%
  stop-loss into a larger percentage move on margin — size positions
  accordingly
- **Choppy market risk:** RSI can hover near 50 for extended periods on
  the 4H chart; the bot stands aside rather than forcing trades
- **Signal lag:** 4H candles mean signals confirm relatively slowly —
  the strategy is not designed for scalping or fast intraday moves

## Agent Execution Flow
1. Pull the latest closed 4H candle's RSI(14) for BTCUSDT and ETHUSDT independently
2. Classify each pair's regime: overbought (>70) / oversold (<30) / neutral (~50)
3. If oversold, scan the 4H chart for "W" double-bottom pattern confirmation before entry
4. If confirmed signal exists, open position with 5–10x leverage
5. Attach stop loss at −19% of capital entry and take-profit at +50–65%
6. If regime = neutral, hold no position and re-check on the next 4H close
7. Monitor both pairs independently and in parallel

## Standard Output Format
Signal: BUY / SELL / HOLD
Pair: BTCUSDT / ETHUSDT
Timeframe: 4H
RSI value: ##
Pattern confirmation: Yes/No
Entry price: $
Stop loss: $ (-19%)
Take profit: $ (+50-65%)
Leverage: 5-10x
