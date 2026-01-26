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
- **🛡️ ¿Por qué una Estrategia Universal?** Aplicamos parámetros idénticos a todos los activos para prevenir el sobreajuste (overfitting). Una estrategia que funciona consistentemente en diversos mercados captura la verdadera dinámica del mercado en lugar de memorizar el ruido histórico, asegurando mayor robustez y fiabilidad en el trading en vivo.
- Se descargan velas históricas vía CCXT para cada par y timeframe.
- Se evalúan resultados con métricas estándar de rendimiento y riesgo (ROI, PF, Max DD, Winrate, etc.).
- All data shown is unleveraged (1x).
- Cada reporte indica si el SL y TP fueron calculados por Porcentaje o por ATR 14,3.
- Usamos **5 TPs**:
  - TP1-TP4: Aseguran ganancias incrementalmente (20% cada uno).
  - **TP5 es nuestro 'Moonbag':** Diseñado para capturar movimientos parabólicos y tendencias extendidas. Al mantener esta porción final activa, la estrategia permanece expuesta a posibles "home runs" sin arriesgar las ganancias ya aseguradas en los TPs anteriores.

## 🏆 Métrica Score
Un valor único que refleja el rendimiento general de la estrategia en tu timeframe seleccionado.

Cuanto mayor sea el Score, más estable y fiable es la estrategia en este timeframe.
Perfecto para comparar rápidamente timeframes y encontrar las mejores configuraciones.

**FÓRMULA:**

Score = ((Profit + 100) / 100) × Winrate² × log(1 + Trades)

Donde:
- **Profit** — beneficio total en todos los TPs
- **Winrate²** — precisión al cuadrado (porque la consistencia gana)
- **log(1 + Trades)** — logaritmo del total de operaciones (no se permite suerte en 2 operaciones)

El resultado:
Alto Beneficio + Winrate Estable + Trading Activo = **MAX SCORE 🏆**

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
