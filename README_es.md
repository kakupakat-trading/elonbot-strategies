# Backtesting y reportes

Este repositorio documenta de forma informativa el flujo de backtesting y reporte.

## Introducción (cómo hacemos el backtesting)
- Corremos backtesting por par y temporalidad con un mínimo de 40,000 velas.
- Exploramos millones de combinaciones internas del indicador para encontrar configuraciones viables.
- Filtramos y seleccionamos solo monedas que cumplan objetivos de rendimiento y riesgo (profit factor y ROI).
- Solo se consideran resultados que califiquen como grado tier1.

## Objetivo
- Validar estrategias con un mínimo de 40,000 velas por par y temporalidad.
- Generar resultados comparables entre monedas y timeframes para construir y refinar la estrategia.

## Metodología (alto nivel)
- Se descargan velas históricas vía CCXT para cada par y timeframe.
- Se evalúan resultados con métricas estándar de rendimiento y riesgo (ROI, PF, Max DD, Winrate, etc.).
- Cada reporte indica si el SL y TP fueron calculados por Porcentaje o por ATR 14,3.
- Usamos 4 TPs: puedes operar cerrando todo en el TP1 o, si prefieres, usar los cuatro TPs con cierres parciales de 50%, 25%, 15% y 10%.

## Flujo de trabajo
- El motor de backtesting consume la lista de estrategias preparada internamente, ejecuta simulaciones históricas y genera el CSV en `backtesting/resultado_backtest.csv`.
- El generador de reportes toma el CSV, limpia columnas técnicas internas y genera un reporte HTML en `report_html/` con:
  - `index.html` con tabla general y gráficas.
  - `images/` con gráficas (ROI y tendencia de accuracy).
  - `details/` con detalle por moneda.

## Estructura de carpetas
- Cada carpeta de trabajo por temporalidad usa el formato `TF_<temporalidad>` (ejemplo: `TF_5m`).
- Los reportes HTML viven en `report_html/` y los CSV en `backtesting/`.

## Estrategias disponibles
- TF_5m
- TF_15m
- TF_30m

## Tiempos estimados
- Aunque se puede escanear todo el mercado, cada moneda tarda ~3 horas en obtener un resultado útil para armar la estrategia.
- En ocasiones puede tardar hasta 6 horas por la cantidad de combinaciones evaluadas.

Prueba sin costo: https://t.me/VIP_Agent_bot?start=m_hEkkwYo
Canal oficial: https://t.me/kakupakat_trading_oficial
