# ADAPTIVE-GOLD-SILVER-BITCOIN-HEDGING-STRATEGY
ADAPTIVE GOLD/SILVER-BITCOIN HEDGING STRATEGY

================================================================================
ADAPTIVE GOLD/SILVER-BITCOIN HEDGING STRATEGY
================================================================================

Author:         QuantLife
Platform:       QuantConnect Lean Algorithm Framework
Version:        2.0
Last Updated:   January 2026

--------------------------------------------------------------------------------
STRATEGY OVERVIEW
--------------------------------------------------------------------------------

This algorithm implements an adaptive trend-following strategy for Bitcoin (BTC)
that uses precious metals (Gold and Silver) as macro risk indicators. The core
thesis is that Gold-BTC correlation is time-varying and regime-dependent:

    - Normal periods:       Correlation ~0.10 (weak positive)
    - Macro risk events:    Correlation ~0.40-0.50 (metals lead by 1-2 days)
    - Explosive bull runs:  Correlation ~0.00 (crypto-specific factors dominate)

By dynamically detecting market phases and adjusting signal weights accordingly,
the strategy aims to:
    1. Capture upside during bullish trends
    2. Reduce exposure before significant drawdowns
    3. Maintain risk-adjusted returns (Sharpe > 1.0)
    4. Limit maximum drawdown to under 20%

--------------------------------------------------------------------------------
METHODOLOGY SUMMARY
--------------------------------------------------------------------------------

1. PHASE DETECTION
   - Classifies BTC into 6 market phases using technical indicators
   - Uses 90-day returns, 30-day volatility, MA relationships, and drawdown
   - 3-day confirmation filter prevents whipsawing

2. SIGNAL GENERATION
   - Precious Metals Signal: Normalized 5d and 20d returns of GLD/SLV
   - Momentum Signal: BTC price momentum relative to moving averages
   - Composite Signal: Weighted combination based on detected phase

3. POSITION SIZING
   - Base position from signal strength (0% to phase maximum)
   - Volatility adjustment using risk parity principles
   - Breakout bonuses and VIX-based adjustments

4. RISK MANAGEMENT
   - Fixed stop loss at -15% from entry
   - Trailing stop: -10% from high after +20% gain
   - Phase-specific position caps
   - Precious metals warning system

--------------------------------------------------------------------------------
COMPETITION REQUIREMENTS
--------------------------------------------------------------------------------

    Starting Capital:   $100,000
    Minimum Sharpe:     1.0
    Maximum Drawdown:   20%
    Backtest Period:    7+ years
    Benchmark:          BTCUSD (crypto strategy)
    Maximum Leverage:   10x (strategy uses max 1x)

--------------------------------------------------------------------------------
REFERENCES
--------------------------------------------------------------------------------

    [1] Historical Gold-BTC correlation analysis (2014-2024)
    [2] Bitcoin market cycle research
    [3] Risk parity portfolio construction principles

================================================================================
