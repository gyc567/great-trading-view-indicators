# great-trading-view-indicators

Custom TradingView indicators and Pine Script utilities.

## Project Structure

```
great-trading-view-indicators/
├── indicators/          # Standalone TradingView indicators (.pine)
├── libraries/           # Shared Pine Script libraries (.pine)
├── .github/workflows/   # CI/CD pipelines
├── CONTRIBUTING.md
├── LICENSE
└── .gitignore
```

## Getting Started

Open any `.pine` file in TradingView's Pine Editor. Indicators in `indicators/` are
ready to add to a chart; library functions in `libraries/` can be imported via
`indicator()` or `strategy()` declarations.

## Available Indicators

### `supertrend_zone_pivot_fib.pine`
**[JL] Supertrend Zone Pivot Point with Zigzag Fib — Optimized Signals**

Multi-signal confirmation indicator combining Supertrend, Fibonacci, and pivot analysis.

**Features:**
- Supertrend (ATR-based) with configurable factor and period
- Premium / Discount ATR zones
- Zigzag pivot point detection with high/low labels
- Fibonacci retracement (0, 0.236, 0.382, 0.5, 0.618, 0.786) + extension levels (1.618, -0.618)
- Optimized Buy/Sell signals with RSI + ADX + HTF multi-filter
- Candle confirmation (bullish/bearish candle filter)
- Signal cooldown (one signal per trend direction)
- Configurable alerts

**Inputs:**
| Group | Parameter | Default |
|---|---|---|
| Supertrend | ATR Length | 10 |
| Supertrend | Factor | 3.0 |
| Supertrend | Premium/Discount Multiplier | 1.5 |
| Signal Filters | Use RSI Filter | true |
| Signal Filters | RSI Length / Overbought / Oversold | 14 / 70 / 30 |
| Signal Filters | Use ADX Filter | true |
| Signal Filters | ADX Length / Threshold | 14 / 20.0 |
| Signal Filters | Min Bars Since Trend Change | 3 |
| Signal Filters | Use HTF Supertrend Filter | false |

**Version:** Pine Script v6

---

### `sma_crossover_rsi.pine`
Basic SMA Crossover with RSI overlay — starter scaffold indicator.

**Features:**
- Fast SMA (configurable period)
- Slow SMA (configurable period)
- RSI pane with overbought/oversold lines
- Visual triangle markers on crossover signals

---

## Available Libraries

_(none yet — see `libraries/` once populated)_

## CI / Validation

Pine Script files are linted via GitHub Actions on push and pull request.
No offline compiler is available — validate by adding the indicator to a TradingView chart.
