# Informe semanal de rendimiento de marketing

Período analizado: **2021-01-25 a 2021-01-31**

Nota metodológica: Windsor devolvió el dataset histórico completo aun cuando se solicitó la semana actual. Para mantener trazabilidad, este informe usa la **última semana realmente disponible en el dataset**: 2021-01-25 a 2021-01-31.

## 1. AUDITORÍA Y COMPRENSIÓN DE DATOS (Data Sanity Check)

- Se recibieron las 15 columnas esperadas y no faltó ninguna columna clave para el análisis.
- No se detectaron valores nulos ni vacíos en las columnas utilizadas para el reporte semanal.
- Las fechas fueron interpretables en el 100% de las filas. El dataset recuperado cubre del **2021-01-01** al **2021-01-31** y la ventana semanal más reciente disponible contiene **730 filas**.
- Los costos vinieron en formato moneda tipo `$12,345.00` y se normalizaron a valor numérico.
- La tasa de conversión vino en formato decimal entre **0.01 y 0.15**; se interpretó como proporción, es decir, `0.08 = 8%`.
- El ROI vino como valor numérico sin símbolo de porcentaje y se interpretó como multiplicador (`x`). Se detectaron **313** filas con ceros a la izquierda en ROI, por ejemplo `07.06`; se normalizaron sin pérdida de valor.
- La duración vino como texto (`15 days`, `30 days`, `45 days`, `60 days`) y se transformó a días numéricos para comparar campañas cortas vs. largas.
- Filas procesadas correctamente para el informe semanal: **730 de 730**. No fue necesario excluir filas del período semanal por problemas de parseo.

## 2. DASHBOARD DE MÉTRICAS GLOBALES (Cálculos de BI)

| Métrica | Resultado semanal |
|---|---:|
| Volumen Total de Impresiones | 4,009,730 |
| ROI Promedio de toda la operación | 5.00x |
| Costo de Adquisición Promedio | $12,408.20 |
| Tasa de Conversión Promedio | 8.00% |

Aclaración: el ROI se reporta como multiplicador promedio y la tasa de conversión como porcentaje derivado del valor decimal original del dataset.

## 3. ANÁLISIS CRUZADO DE EFICIENCIA (Insights de Negocio)

**Conclusión ejecutiva:** en la última semana disponible, **Google Ads** fue el canal más sólido en retorno total, mientras que **Website** fue el más balanceado en eficiencia de conversión y costo. La mejor combinación específica con evidencia repetida fue **Email + Men 25-34 + Display**.

- **Mejor combinación Channel_Used + Target_Audience + Campaign_Type:** `Email + Men 25-34 + Display` con **3 campañas**, **ROI promedio de 7.51x**, **conversión promedio de 8.67%** y **costo promedio de adquisición de $16,151.00**. Se considera la mejor combinación específica porque lidera en ROI entre las combinaciones con al menos 3 observaciones, evitando basarse en un caso aislado.
- **Respuesta a campañas largas vs. cortas por Customer_Segment:** `Tech Enthusiasts` reaccionó mejor a campañas largas, con ROI de **4.84x** vs. **4.61x** en campañas cortas y conversión de **8.43%** vs. **7.39%**. En cambio, `Outdoor Adventurers` rindió mejor con campañas cortas, con ROI de **5.23x** vs. **5.14x** y conversión de **8.12%** vs. **7.24%**.
- **Respuesta a campañas largas vs. cortas por Location:** `Chicago` respondió mejor a campañas largas por ROI, con **5.02x** frente a **4.76x** en campañas cortas. `New York` respondió mejor a campañas cortas, con **5.05x** frente a **4.93x** y una conversión de **8.52%** frente a **7.51%**.
- **Relación entre Engagement_Score y ROI:** el coeficiente de correlación de Pearson fue **0.015**, por lo que no muestra una correlación visible relevante. En este dataset semanal, un engagement alto no garantiza un ROI alto.
- **Conclusión explícita sobre el mejor canal:** `Google Ads` fue el mejor canal por retorno promedio, con **ROI de 5.32x** en **124 campañas** y **726,555 impresiones**. `Website` quedó muy cerca en ROI (**5.12x**), pero con mejor conversión (**8.40%**) y costo más bajo (**$12,246.67**), así que es el canal alternativo más eficiente para escalar. `YouTube` fue el canal más débil en ROI promedio (**4.78x**), aunque no en conversión.

## 4. PLAN DE ACCIÓN RECOMENDADO (Decisiones de Negocio)

1. **Reasignar presupuesto incremental hacia Google Ads y Website, con foco en audiencias de rendimiento probado.** Mueve parte del presupuesto de canales con menor retorno hacia `Google Ads` y `Website`, priorizando campañas para `Men 25-34`, `Tech Enthusiasts` y geografías como `Chicago` y `Los Angeles`, porque Google Ads lideró el ROI semanal (**5.32x**) y Website combinó un ROI alto con mejor conversión y costo controlado.
2. **Escalar el patrón ganador `Email + Men 25-34 + Display` como célula táctica del próximo mes.** Replica esa combinación en nuevas variantes creativas y de oferta, financiándola con reducción parcial en `YouTube` y en campañas de `Facebook` de bajo retorno relativo. La base es concreta: esa combinación sostuvo **3 observaciones**, con **ROI de 7.51x** y **8.67%** de conversión, muy por encima del promedio semanal.
3. **Separar la estrategia de duración por segmento y ubicación en lugar de usar una sola cadencia para todos.** Mantén campañas largas para `Tech Enthusiasts` y mercados como `Chicago`, donde mejoró el ROI, y reduce campañas largas en `Outdoor Adventurers` y `New York`, donde las campañas cortas respondieron mejor. La reasignación debe salir de formatos largos menos eficientes y moverse a secuencias cortas en esos segmentos y ubicaciones, porque el dataset muestra diferencias observables de rendimiento por duración.
