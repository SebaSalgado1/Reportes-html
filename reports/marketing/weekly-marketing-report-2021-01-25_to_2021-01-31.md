# Informe semanal de rendimiento de marketing

Período solicitado por la ejecución programada: 18 al 24 de mayo de 2026.

Período realmente disponible en Windsor y analizado para este informe: 25 al 31 de enero de 2021.

## 1. AUDITORÍA Y COMPRENSIÓN DE DATOS (Data Sanity Check)

- Se recuperaron 3,432 filas desde Windsor y se procesaron correctamente 730 filas correspondientes a la última semana completa disponible en la fuente: 2021-01-25 a 2021-01-31.
- No se detectaron valores nulos ni vacíos en las columnas clave analizadas: `campaign_type`, `target_audience`, `duration`, `channel_used`, `conversion_rate`, `acquisition_cost`, `roi`, `location`, `clicks`, `impressions`, `engagement_score`, `customer_segment` y `date`.
- No hubo fallas de parseo en fechas, costos, tasas, impresiones, clics, engagement ni duración.
- La convención usada para tasas es decimal: por ejemplo, `0.08 = 8%`.
- Se detectaron formatos heterogéneos pero consistentes y utilizables:
  - `acquisition_cost` viene como moneda en texto, por ejemplo `$13,766.00`.
  - `duration` viene como texto, por ejemplo `15 days`, `30 days`, `45 days`, `60 days`.
  - `roi`, `conversion_rate`, `clicks`, `impressions` y `engagement_score` llegan como texto aunque representan métricas numéricas.
- No existe una columna de ID de campaña en el dataset, por lo que no fue posible auditar consistencia de IDs.
- No fue necesario excluir filas dentro de la semana analizada.
- Limitación crítica: Windsor no entregó datos para la semana cerrada más reciente del calendario actual, sino solo datos entre 2021-01-01 y 2021-01-31. Por eso este reporte semanal usa la última semana completa realmente disponible en la fuente.

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

- La combinación con mayor ROI puntual fue `Email + Men 25-34 + Display`, con ROI promedio de 7.51, pero sobre solo 3 registros y con costo de adquisición promedio alto de $16,151.
- Si se prioriza retorno con mejor eficiencia operativa y un mínimo de mayor estabilidad muestral, la mejor combinación observada fue `Google Ads + Women 25-34 + Influencer`: 4 registros, ROI promedio de 7.24, costo de adquisición promedio de $7,339 y tasa de conversión promedio de 10.75%. En la práctica, esta combinación ofrece una relación más sólida entre rentabilidad, costo y conversión que el máximo ROI puntual.
- En duración de campañas, la señal más clara por segmento favorece campañas largas:
  - `Tech Enthusiasts`: ROI promedio de 4.84 en campañas largas vs 4.61 en cortas.
  - `Fashionistas`: ROI promedio de 5.19 en campañas largas vs 4.97 en cortas.
- La principal excepción por segmento fue `Outdoor Adventurers`, donde las campañas cortas rindieron mejor: ROI promedio de 5.23 en cortas vs 5.14 en largas.
- Por ubicación, las campañas largas reaccionaron mejor en:
  - `Chicago`: ROI promedio de 5.02 en largas vs 4.76 en cortas.
  - `Los Angeles`: ROI promedio de 5.05 en largas vs 4.84 en cortas.
  - `Miami`: ROI promedio de 5.24 en largas vs 5.09 en cortas.
- La ubicación con preferencia más visible por campañas cortas fue `New York`: ROI promedio de 5.05 en cortas vs 4.93 en largas.
- No existe una correlación visible entre `Engagement_Score` y `ROI`. La correlación de Pearson observada fue 0.015, esencialmente nula para fines ejecutivos. Eso indica que un mayor engagement en este dataset no está anticipando mejor rentabilidad.
- La conclusión explícita sobre el mejor canal es `Google Ads`. Fue el canal con mejor ROI promedio semanal (5.32), con costo de adquisición promedio ligeramente por debajo del promedio global ($12,308.74 vs $12,408.20) y mejor desempeño agregado que Facebook, Email, Instagram y YouTube. `Website` quedó segundo en ROI (5.12) y mostró una conversión media ligeramente superior, pero no superó a Google Ads en retorno total de eficiencia.
- El canal más débil en retorno agregado fue `YouTube`, con ROI promedio de 4.78. Además, varias de sus combinaciones aparecen entre las de menor rendimiento de la semana, por ejemplo `YouTube + Men 18-24 + Display` con ROI promedio de 3.70 y `YouTube + Women 35-44 + Influencer` con ROI promedio de 3.90.

## 4. PLAN DE ACCIÓN RECOMENDADO (Decisiones de Negocio)

1. Reasignar presupuesto incremental hacia `Google Ads`, en especial en la combinación `Women 25-34 + Influencer`, y sostener apoyo secundario en `Website` para captura y conversión. La razón es directa: Google Ads fue el mejor canal agregado de la semana (ROI 5.32) y esa combinación específica logró ROI 7.24 con un costo de adquisición muy eficiente de $7,339. La fuente de presupuesto debería salir primero de `YouTube`, que cerró como el canal con menor ROI promedio (4.78).
2. Extender campañas de más de 30 días para `Fashionistas`, `Tech Enthusiasts`, `Chicago`, `Los Angeles` y `Miami`, y reducir el peso de duraciones largas en `Outdoor Adventurers` y `New York`. La observación concreta es que las campañas largas dieron una mejora visible de ROI en esos segmentos y ubicaciones, mientras que en `Outdoor Adventurers` y `New York` la respuesta fue mejor en campañas cortas.
3. Reducir decisiones de inversión basadas en `Engagement_Score` y mover ese criterio hacia ROI, conversión y costo de adquisición por combinación. Como la correlación `Engagement_Score`-`ROI` fue prácticamente nula (0.015), conviene pausar o moderar combinaciones que sostienen engagement sin retorno superior, como varias ejecuciones de `YouTube` y `Instagram + Men 25-34 + Search` (ROI 3.46 con 10 registros), y redirigir ese presupuesto a combinaciones de `Google Ads` y `Website` que sí mostraron eficiencia económica real.
