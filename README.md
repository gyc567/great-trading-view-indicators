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

### `jl_trap_system.pine`
**JL + Trap 高胜率系统（反转 + 顺势 + 未来潜在反转区）**

High-probability trading system combining Supertrend, Trap channel (EMAfi ATR envelope),
and Fibonacci levels to detect reversals and trend-following entries.

**Features:**
- Supertrend (ATR-based) with configurable factor and period
- Premium / Discount ATR zones
- Trap channel (EMA + ATR envelope) — detects bear/bull trap setups
- Fibonacci retracement (0, 0.5, 0.618, 0.786) + extension (1.618, -0.618)
- Small-trend pivot high/low labels on direction turns
- Potential Reversal Zones (PRZ) — resistance and support boxes
- Reversal signals: Trap + RSI probability + Supertrend direction confirmation
- Trend-following signals: Supertrend + Fib Gold zone + candle confirmation
- Built-in SL/TP lines (dashed/dotted) with R:R ratio display
- Detailed entry labels: probability, entry, SL, TP1, TP2, RR ratio
- Signal cooldown to prevent over-trading
- 4 independent alert conditions

**Inputs:**
| Group | Parameter | Default |
|---|---|---|
| Supertrend | ATR Length | 10 |
| Supertrend | Factor | 3.0 |
| Supertrend | 折扣/溢价倍数 | 1.5 |
| Trap | 通道平滑长度 | 55 |
| Trap | 通道宽度倍数 | 2.5 |
| Trap | Trap 窗口 | 8 |
| Trap | 反转最低概率% | 55 |
| 高胜率过滤 | 启用 RSI 过滤 | true |
| 高胜率过滤 | RSI 长度 / 超买 / 超卖 | 14 / 68 / 32 |
| 高胜率过滤 | 启用 ADX 趋势过滤 | true |
| 高胜率过滤 | ADX 长度 / 最小值 | 14 / 16.0 |
| 高胜率过滤 | 最低风险回报比 | 1.4 |
| 高胜率过滤 | 信号冷却K线 | 5 |

**Signal Types:**
| Signal | Color | Trigger |
|---|---|---|
| 反转开多 (Reversal Long) | Aqua | Bull trap + RSI prob ≥ min + ST direction flip |
| 反转开空 (Reversal Short) | Fuchsia | Bear trap + RSI prob ≥ min + ST direction flip |
| 顺势开多 (Trend Long) | Lime | ST downtrend + discount zone + Fib Gold Long |
| 顺势开空 (Trend Short) | Red | ST uptrend + premium zone + Fib Gold Short |

**Version:** Pine Script v6

---

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

**Version:** Pine Script v5

---

## Available Libraries

_(none yet — see `libraries/` once populated)_

## CI / Validation

Pine Script files are linted via GitHub Actions on push and pull request.
No offline compiler is available — validate by adding the indicator to a TradingView chart.
