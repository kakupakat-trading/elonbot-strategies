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
- All data shown is unleveraged (1x).
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

## Páginas de estrategias
Reportes HTML por temporalidad:

### TF_5m
- Carpeta: `TF_5m/`
- Reporte: https://kakupakat-trading.github.io/elonbot-strategies/TF_5m/
- Notas: _Agrega resumen o conclusiones aquí._

### TF_15m
- Carpeta: `TF_15m/`
- Reporte: https://kakupakat-trading.github.io/elonbot-strategies/TF_15m/
- Notas: _Agrega resumen o conclusiones aquí._

### TF_30m
- Carpeta: `TF_30m/`
- Reporte: https://kakupakat-trading.github.io/elonbot-strategies/TF_30m/
- Notas: _Agrega resumen o conclusiones aquí._

## Tiempos estimados
- Aunque se puede escanear todo el mercado, cada moneda tarda ~3 horas en obtener un resultado útil para armar la estrategia.
- En ocasiones puede tardar hasta 6 horas por la cantidad de combinaciones evaluadas.

## Framework Atlas AI
Atlas AI no es solo un simple bot de indicadores; es un motor de decisión cuantitativa híbrido que combina modelado técnico avanzado con validación de Inteligencia Artificial. Opera en cuatro etapas críticas:

1. **Escaneo de Mercado (The Scanner)**: El sistema monitorea Binance Futures en tiempo real, aplicando filtros dinámicos para aislar activos de alta liquidez y descartar mercados muertos o susceptibles.
2. **El Motor Matemático (The Mathematical Engine)**: Aquí reside la lógica propietaria. El algoritmo utiliza modelado estadístico multifactorial y análisis de coherencia de momentum para detectar anomalías de mercado de alta probabilidad, distinguiendo movimientos estructurales genuinos del ruido de mercado y "falsas rupturas".
3. **Validación por IA (The Brain)**: Este es el cambio de juego. Una vez que el modelo cuantitativo detecta una señal potencial, se envía a un módulo de Validación LLM (Modelo de Lenguaje Grande). La IA analiza el contexto completo del mercado para aprobar o rechazar la operación, actuando como un gestor de riesgo senior que filtra falsos positivos.
4. **Ejecución y Transparencia**: Si la IA aprueba la operación, Atlas calcula parámetros de riesgo dinámicos basados en la volatilidad en tiempo real (tamaño adaptativo) y transmite la operación a nuestros canales, asegurando total transparencia.

Prueba sin costo: https://t.me/VIP_Agent_bot?start=m_hEkkwYo
Canal oficial: https://t.me/kakupakat_trading_oficial

#tradingview #indicator #algo #tradingview-strategy #strategy #code #pinescript #crypto #bitcoin #download #telegram #predictum #ggshot
