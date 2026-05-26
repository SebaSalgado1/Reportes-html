# Informe Semanal de Rendimiento de Marketing

Período analizado: 2021-01-25 a 2021-01-31

Nota de alcance: la ejecución se realizó el 2026-05-26, pero el dataset recuperado desde Windsor solo contiene información hasta el 2021-01-31. Por precisión, este informe usa la última semana completa realmente disponible en los datos.

1. AUDITORÍA Y COMPRENSIÓN DE DATOS (Data Sanity Check)

- Se recuperaron 3,432 filas totales desde Windsor y se aislaron 730 filas correspondientes a la última semana disponible: 2021-01-25 a 2021-01-31.
- Las 15 columnas analíticas esperadas estuvieron presentes: `company`, `campaign_type`, `target_audience`, `duration`, `channel_used`, `conversion_rate`, `acquisition_cost`, `roi`, `location`, `language`, `clicks`, `impressions`, `engagement_score`, `customer_segment` y `date`.
- No se detectaron valores nulos ni celdas vacías en las 730 filas semanales utilizadas.
- Las fechas fueron consistentes y parseables en formato `YYYY-MM-DD`. No hubo filas excluidas por errores de fecha.
- `Conversion_Rate` vino en formato decimal entre 0 y 1. En este informe se interpreta como proporción: por ejemplo, `0.08 = 8.0%`.
- `Acquisition_Cost` vino en formato monetario con símbolo `$` y separadores de miles; fue normalizado a valor numérico sin pérdidas.
- `ROI` vino como texto y en algunos registros del mes completo aparecieron ceros a la izquierda como `07.06` o `02.05`. En la semana analizada no hubo errores de parseo y todos los valores fueron convertidos correctamente a numérico.
- `Duration` vino como texto (`15 days`, `30 days`, `45 days`, `60 days`) y se normalizó a días para el análisis. Para comparar duraciones, se definió `corta = 15-30 días` y `larga = 45-60 días`.
- Limitación relevante: el dataset está desactualizado frente a la fecha de ejecución. No fue posible construir un informe de mayo de 2026 porque Windsor no devolvió datos de ese período.
- Total de filas procesadas correctamente para métricas globales: 730 de 730.

2. DASHBOARD DE MÉTRICAS GLOBALES (Cálculos de BI)

| Métrica | Resultado |
| --- | ---: |
| Volumen Total de Impresiones | 4,009,730 |
| ROI Promedio de toda la operación | 5.00 |
| Costo de Adquisición Promedio | $12,408.20 |
| Tasa de Conversión Promedio | 8.00% |

Convención usada: la tasa de conversión se presenta en porcentaje, aunque el dataset original la entrega en decimales.

3. ANÁLISIS CRUZADO DE EFICIENCIA (Insights de Negocio)

- La mejor combinación específica de `Channel_Used + Target_Audience + Campaign_Type` fue `Google Ads + Women 25-34 + Display`, con ROI promedio de 6.65, costo de adquisición promedio de $12,804.40 y tasa de conversión promedio de 6.40% en 5 registros. Es la combinación con mejor retorno observado dentro de las combinaciones con al menos 5 casos, aunque el tamaño de muestra es más liviano que el de los canales agregados.
- El mejor canal de la semana fue `Google Ads`. Registró el ROI promedio más alto entre canales (5.32) sobre 124 filas, con costo de adquisición promedio de $12,308.74 y 726,555 impresiones. `Website` quedó cerca en segundo lugar con ROI promedio de 5.12 y un costo algo menor ($12,246.67), pero sin superar a Google Ads en retorno.
- En contraste, `YouTube` fue el canal con peor ROI promedio (4.78) en la semana, aun cuando mostró una tasa de conversión relativamente alta (8.62%). Eso sugiere que convertir más no necesariamente se tradujo en mejor rentabilidad en este corte.
- Por tipo de campaña, las mejores duplas canal-campaña fueron `Google Ads + Search` (ROI 5.85, CAC $11,832.63, 19 filas), `Website + Social Media` (ROI 5.40, CAC $11,782.00, 29 filas) y `Google Ads + Influencer` (ROI 5.38, CAC $11,336.12, 25 filas).
- Entre los focos de menor eficiencia aparecieron `YouTube + Influencer` (ROI 4.04, 20 filas), `Instagram + Social Media` (ROI 4.28, 28 filas) y `Facebook + Foodies` a nivel segmento-canal (ROI 4.20, 18 filas).
- En segmentación por duración, `Tech Enthusiasts` reaccionó mejor a campañas largas: el ROI promedio subió de 4.61 a 4.84 y la conversión promedio de 7.39% a 8.43%, además de bajar el CAC de $13,428.56 a $11,694.18. En cambio, `Outdoor Adventurers` respondió mejor a campañas cortas: el ROI cayó de 5.23 a 5.14 cuando la duración pasó a larga y la conversión también bajó de 8.12% a 7.24%.
- En ubicación, `Chicago` reaccionó mejor a campañas largas: el ROI promedio subió de 4.76 a 5.02 y el CAC bajó de $12,478.59 a $11,736.13. `New York` mostró la señal inversa: las campañas cortas rindieron mejor, con ROI promedio de 5.05 frente a 4.93 en campañas largas y una conversión promedio de 8.52% frente a 7.51%.
- La correlación visible entre `Engagement_Score` y `ROI` fue prácticamente nula. El coeficiente de correlación de Pearson fue 0.0148, así que no hay evidencia en esta semana para usar engagement como predictor directo de rentabilidad.

4. PLAN DE ACCIÓN RECOMENDADO (Decisiones de Negocio)

1. Reasignar presupuesto incremental hacia `Google Ads`, priorizando campañas `Search` e `Influencer`, y recortar inversión en `YouTube + Influencer` e `Instagram + Social Media`. La evidencia es clara: `Google Ads + Search` logró ROI 5.85 con CAC de $11,832.63 y `Google Ads + Influencer` ROI 5.38 con CAC de $11,336.12, mientras `YouTube + Influencer` cayó a ROI 4.04 e `Instagram + Social Media` a 4.28.
2. Escalar `Website` como segundo canal prioritario, especialmente en campañas `Social Media` y sobre el segmento `Outdoor Adventurers`, y reducir exposición de `Facebook` en `Foodies` y `Tech Enthusiasts`. `Website + Social Media` rindió ROI 5.40 con CAC de $11,782.00, y `Website + Outdoor Adventurers` llegó a ROI 5.58 con conversión de 9.93%. En cambio, `Facebook + Foodies` bajó a ROI 4.20 y `Facebook + Tech Enthusiasts` a 4.38, con costos más tensos.
3. Ajustar la duración de campaña por audiencia y ubicación en vez de usar una regla uniforme. Para el próximo mes, conviene sostener campañas largas de `Google Ads` y `Website` sobre `Tech Enthusiasts` y en `Chicago`, donde la duración larga elevó ROI y redujo CAC. En paralelo, conviene pausar o reducir campañas largas en `New York` y sobre `Outdoor Adventurers`, y mover ese presupuesto hacia formatos cortos de 15-30 días en esos frentes, porque allí las campañas cortas mostraron mejor ROI y mejor conversión.
