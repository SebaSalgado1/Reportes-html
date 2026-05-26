# Informe semanal de rendimiento de marketing

Período solicitado por la ejecución semanal: 2026-05-18 a 2026-05-24.

Período realmente disponible en Windsor y analizado en esta ejecución: 2021-01-25 a 2021-01-31.

## 1. AUDITORÍA Y COMPRENSIÓN DE DATOS (Data Sanity Check)

- Se recuperaron 3,432 filas desde Windsor y se procesaron correctamente 730 filas correspondientes a la última semana completa disponible en la fuente: 2021-01-25 a 2021-01-31.
- No se detectaron valores nulos ni vacíos en las columnas clave analizadas: `campaign_type`, `target_audience`, `duration`, `channel_used`, `conversion_rate`, `acquisition_cost`, `roi`, `location`, `clicks`, `impressions`, `engagement_score`, `customer_segment` y `date`.
- No hubo fallas de parseo en fechas, costos, tasas, clics, impresiones, engagement ni duración; por eso no fue necesario excluir filas dentro de la semana analizada.
- La convención usada para tasas es decimal: `0.08 = 8%`.
- Se detectó una inconsistencia de formato relevante pero utilizable: 62 registros semanales de `roi` llegaron con cero a la izquierda, por ejemplo `07.06`. Se normalizaron a valor numérico antes del cálculo.
- `acquisition_cost` llega como moneda en texto y `duration` como texto tipo `15 days`, pero ambos formatos fueron consistentes y convertibles en toda la semana.
- No existe una columna de ID de campaña en el dataset, por lo que no fue posible auditar consistencia de IDs.
- Limitación crítica: Windsor no entregó datos recientes del calendario actual. La fecha máxima disponible fue 2021-01-31, así que este informe semanal usa la última semana completa realmente disponible en la fuente y no la semana cerrada más reciente de mayo de 2026.

## 2. DASHBOARD DE MÉTRICAS GLOBALES (Cálculos de BI)

| Métrica | Resultado |
| --- | ---: |
| Volumen Total de Impresiones | 4,009,730 |
| ROI Promedio de toda la operación | 5.00 |
| Costo de Adquisición Promedio | $12,408.20 |
| Tasa de Conversión Promedio | 8.00% |

Notas de cálculo:

- El ROI promedio se calculó sobre las 730 filas semanales válidas.
- La tasa de conversión promedio se reporta como porcentaje luego de interpretar `conversion_rate` en formato decimal.

## 3. ANÁLISIS CRUZADO DE EFICIENCIA (Insights de Negocio)

- La combinación con mejor balance entre retorno y eficiencia fue `Google Ads + Women 25-34 + Influencer`: 4 registros, ROI promedio de 7.24, tasa de conversión promedio de 10.75% y costo de adquisición promedio de $7,339. Es la mejor combinación observable cuando se ponderan rentabilidad, conversión y costo al mismo tiempo.
- La combinación con mayor ROI puntual fue `Email + Men 25-34 + Display`, con ROI promedio de 7.51, pero sobre solo 3 registros y con costo de adquisición promedio más alto de $16,151, por lo que su eficiencia económica fue inferior a la combinación líder de Google Ads.
- Por segmento, las campañas largas reaccionaron mejor en `Tech Enthusiasts` (ROI 4.84 vs 4.61 en cortas), `Fashionistas` (5.19 vs 4.97) y `Health & Wellness` (5.15 vs 5.04). La principal excepción fue `Outdoor Adventurers`, donde las campañas cortas rindieron mejor (5.23 vs 5.14).
- Por ubicación, las campañas largas reaccionaron mejor en `Chicago` (ROI 5.02 vs 4.76 en cortas), `Los Angeles` (5.05 vs 4.84) y `Miami` (5.24 vs 5.09). `New York` fue la señal más clara a favor de campañas cortas (5.05 vs 4.93).
- No existe una correlación visible entre `Engagement_Score` y `ROI`. La correlación de Pearson observada fue 0.015, esencialmente nula para fines ejecutivos, así que mayor engagement no anticipó mejor rentabilidad en esta semana.
- La conclusión explícita sobre el mejor canal es `Google Ads`. Lideró el ROI promedio semanal con 5.32 sobre 124 campañas, mantuvo un costo de adquisición promedio de $12,308.74, apenas mejor que el promedio global, y sostuvo suficiente volumen para que la señal no dependa de pocos casos. `Website` quedó segundo en ROI con 5.12 y mostró una conversión media levemente superior, pero no superó a Google Ads en retorno agregado.
- El canal más débil en retorno agregado fue `YouTube`, con ROI promedio de 4.78. Además, varias combinaciones de bajo desempeño de la semana salieron de ese canal, como `YouTube + Men 18-24 + Display` (ROI 3.70) y `YouTube + Women 35-44 + Influencer` (ROI 3.90).

## 4. PLAN DE ACCIÓN RECOMENDADO (Decisiones de Negocio)

1. Reasignar presupuesto incremental hacia `Google Ads`, con prioridad en `Women 25-34 + Influencer`, y sostener apoyo secundario en `Website` para captura y conversión. La base es directa: Google Ads fue el mejor canal agregado de la semana y esa combinación específica logró ROI 7.24 con CAC de $7,339 y conversión de 10.75%. El primer origen del presupuesto debe ser `YouTube`, que cerró como el canal con menor ROI promedio.
2. Extender campañas de 45 a 60 días para `Tech Enthusiasts`, `Fashionistas`, `Health & Wellness`, `Chicago`, `Los Angeles` y `Miami`, y reducir duraciones largas en `Outdoor Adventurers` y `New York`. La observación concreta es que las campañas largas mejoraron el ROI en esos segmentos y ubicaciones, mientras que en `Outdoor Adventurers` y `New York` la señal fue la opuesta.
3. Reducir decisiones de inversión basadas en `Engagement_Score` y mover el criterio principal a ROI, conversión y CAC por combinación. Como la correlación `Engagement_Score`-`ROI` fue prácticamente nula, conviene moderar combinaciones que sostienen gasto sin retorno alto, como `Instagram + Men 25-34 + Search` con ROI 3.46 sobre 10 registros y varias ejecuciones de `YouTube`, para redirigir ese presupuesto a combinaciones de `Google Ads` y `Website` con evidencia de eficiencia económica real.
