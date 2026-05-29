# Alpha-Dairy Quant Pipeline

## Architecture & State
- Database: SQLite time-series data store located at `data/db/market_intelligence.db`.
- Backtest Engine: Pure Python mathematical arrays using NumPy and Pandas.
- Visualizations: Charts rendered via Matplotlib/Seaborn and exported as high-res PNGs to `data/exports/`.

## Tables & Schema Expectations
- `usda_dairy_pools`: columns -> `timestamp (TEXT)`, `product_series (TEXT)`, `price_per_lb (REAL)`, `volume_lbs (REAL)`, `region (TEXT)`.
- `backtest_logs`: columns -> `strategy_name (TEXT)`, `sharpe_ratio (REAL)`, `max_drawdown (REAL)`, `total_return (REAL)`, `execution_timestamp (TEXT)`.

## Execution Discipline
- Use `execute_code` in `project` mode for running backtests and rendering charts to maintain virtualenv access.
- Every report generation must save a clean data log as a `.csv` and a chart as a `.png` file inside `data/exports/`.
- Final turn outputs meant for messaging platforms must terminate with the plain-text absolute paths of the generated assets and include the `[[as_document]]` token to preserve original byte layouts.
