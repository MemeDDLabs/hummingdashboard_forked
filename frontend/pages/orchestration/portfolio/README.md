# Portfolio Management

The Portfolio Management page provides comprehensive oversight of your trading portfolio across multiple exchanges, accounts, and strategies.

## Features

### ₿ Multi-Exchange Portfolio

- **Unified Balance View**: Aggregate holdings across all connected exchanges
- **Real-time Valuation**: Live portfolio value updates in USD and BTC
- **Asset Distribution**: Visual breakdown of holdings by asset and exchange
- **Historical Performance**: Track portfolio value over time

### 📈 Position Tracking

- **Open Positions**: Monitor all active positions across exchanges
- **P&L Analysis**: Real-time and realized profit/loss calculations
- **Risk Metrics**: Position sizing, leverage, and exposure analysis
- **Position History**: Complete record of closed positions

### 🚀 Performance Analytics

- **ROI Calculation**: Return on investment by strategy and timeframe
- **Sharpe Ratio**: Risk-adjusted performance metrics
- **Win Rate Analysis**: Success rate of trades by strategy
- **Drawdown Tracking**: Maximum and current drawdown monitoring

### 🛡️ Risk Management

- **Exposure Limits**: Set and monitor position size limits
- **Correlation Analysis**: Identify correlated positions
- **VaR Calculation**: Value at Risk across the portfolio
- **Alert System**: Notifications for risk threshold breaches

## Usage Instructions

### 1. Connect Exchanges

- Navigate to the Credentials page to add exchange API keys
- Ensure API keys have read permissions for balances and positions
- Verify successful connection in the portfolio overview

### 2. Portfolio Overview

- **Total Value**: View aggregate portfolio value in preferred currency
- **Asset Allocation**: Pie chart showing distribution across assets
- **Exchange Distribution**: Breakdown of holdings by exchange
- **24h Performance**: Daily change in portfolio value

### 3. Position Management

- **Active Positions Tab**: Current open positions with live P&L
- **Position Details**: Click any position for detailed metrics
- **Quick Actions**: Close positions or adjust sizes
- **Export Data**: Download position data for external analysis

### 4. Performance Analysis

- **Time Range Selection**: Choose analysis period (1D, 1W, 1M, 3M, 1Y)
- **Strategy Breakdown**: Performance attribution by strategy
- **Benchmark Comparison**: Compare against BTC or market indices
- **Custom Reports**: Generate detailed performance reports

### 5. Risk Monitoring

- **Risk Dashboard**: Overview of key risk metrics
- **Position Sizing**: Ensure positions align with risk limits
- **Correlation Matrix**: Visualize position correlations
- **Stress Testing**: Simulate portfolio under various scenarios

## Technical Notes

### Data Architecture

- **Real-time Updates**: WebSocket connections for live data
- **Data Aggregation**: Efficient cross-exchange data consolidation
- **Historical Storage**: Time-series database for performance tracking
- **Cache Layer**: Redis caching for improved performance

### Calculation Methods

- **Portfolio Value**: Sum of all holdings at current market prices
- **Unrealized P&L**: (Current Price - Entry Price) × Position Size
- **Realized P&L**: Actual profits from closed positions
- **ROI**: (Current Value - Initial Value) / Initial Value × 100

### Performance Optimization

- **Incremental Updates**: Only fetch changed data
- **Batch Processing**: Aggregate API calls across exchanges
- **Smart Caching**: Cache static data with TTL
- **Lazy Loading**: Load detailed data on demand

## Component Structure

```
portfolio/
├── app.py                      # Main portfolio page
├── components/
│   ├── portfolio_overview.py   # Summary cards and charts
│   ├── position_table.py       # Active positions display
│   ├── performance_charts.py   # Performance visualization
│   └── risk_dashboard.py       # Risk metrics and alerts
├── services/
│   ├── balance_aggregator.py   # Multi-exchange balance fetching
│   ├── position_tracker.py     # Position monitoring service
│   └── performance_calc.py     # Performance calculations
└── utils/
    ├── currency_converter.py   # FX rate conversions
    ├── risk_metrics.py         # Risk calculation functions
    └── data_export.py          # Export functionality
```

## Key Metrics Explained

### Portfolio Metrics

- **Total Value**: Sum of all assets converted to base currency
- **Daily Change**: 24-hour change in portfolio value
- **All-Time P&L**: Total profit/loss since inception
- **Asset Count**: Number of unique assets held

### Position Metrics

- **Entry Price**: Average price of position entry
- **Mark Price**: Current market price
- **Unrealized P&L**: Paper profit/loss on open position
- **ROI %**: Return on investment percentage

### Risk Metrics

- **Sharpe Ratio**: Risk-adjusted return metric
- **Maximum Drawdown**: Largest peak-to-trough decline
- **Value at Risk (VaR)**: Potential loss at confidence level
- **Exposure**: Total position size relative to portfolio

## Best Practices

### Portfolio Management

- Diversify across multiple assets and strategies
- Set position size limits based on risk tolerance
- Regular rebalancing to maintain target allocations
- Monitor correlation between positions

### Performance Tracking

- Record all trades for accurate P&L calculation
- Include fees in performance calculations
- Compare performance against relevant benchmarks
- Regular performance attribution analysis

### Risk Control

- Set stop-loss levels for all positions
- Monitor leverage usage across accounts
- Regular stress testing of portfolio
- Maintain cash reserves for opportunities

## Error Handling

The portfolio page includes robust error handling:

- **API Failures**: Graceful degradation with cached data
- **Rate Limiting**: Intelligent request throttling
- **Data Inconsistencies**: Reconciliation mechanisms
- **Connection Issues**: Automatic reconnection with exponential backoff
- **Calculation Errors**: Fallback values with warning indicators
