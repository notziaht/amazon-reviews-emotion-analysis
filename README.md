# 🎭 Detección de Emociones en Reseñas de Amazon

Sistema de detección de emociones específicas en reseñas de productos Amazon usando procesamiento distribuido con **PySpark** y clasificación con **Spark MLlib + DistilBERT**.

> **Grupo 1** · Tais Guadalupe Carreño Peñaherreta · Camila Doménica Loarte Aguilar

---

## 📌 Descripción

Las plataformas de e-commerce como Amazon reciben millones de reseñas diarias, pero los sistemas actuales solo realizan análisis de sentimientos genéricos (positivo/negativo). Este proyecto va más allá, identificando automáticamente **4 emociones específicas** en cada reseña:

| Emoción | Implicación de negocio |
|---|---|
| 😤 Frustración | Alto riesgo de devoluciones y daño reputacional |
| 😞 Decepción | Indica brecha entre expectativa y producto |
| 😊 Alegría | Señal de experiencia positiva replicable |
| 🤝 Confianza | Mayor potencial de recompra y recomendación |

---

## 🎯 Objetivo

Desarrollar un pipeline de detección de emociones con **precisión superior al 80%**, capaz de procesar reseñas en escala, permitiendo a gerentes de producto priorizar mejoras basadas en las emociones más frecuentes.

---

## 📊 Dataset

**Amazon Reviews Dataset** — [Kaggle](https://www.kaggle.com/datasets/danielihenacho/amazon-reviews-dataset)

| Campo | Detalle |
|---|---|
| Registros | 17,341 reseñas |
| Columnas | `sentiment`, `cleaned_review`, `cleaned_review_length`, `review_score` |
| Formato | CSV |
| Variable objetivo | `emotion_detected` (decepción, frustración, alegría, confianza, neutral) |

---

## 🏗️ Arquitectura del Pipeline

```
CSV (Amazon Reviews)
        │
        ▼
[1] Carga y validación con PySpark
        │
        ▼
[2] EDA: distribución, estadísticas, correlaciones
        │
        ▼
[3] DistilBERT Zero-Shot Classification
        │  → clasifica 4 emociones por reseña
        ▼
[4] Enriquecimiento: probabilidades + correlación con score/sentiment
        │
        ▼
[5] Exportación Parquet + Visualizaciones
```

**Columnas de salida:** `cleaned_review`, `emotion_detected`, `emotion_probability`, `review_score`, `sentiment`

---

## ⚙️ Tecnologías

- **PySpark** — procesamiento distribuido
- **Spark MLlib** — pipeline de clasificación
- **DistilBERT** (Zero-Shot Classification) — modelo de emociones
- **Parquet** — formato de salida optimizado

---

## 📈 Objetivos Específicos

1. **EDA con PySpark**: distribución de sentimientos, estadísticas de longitud de reseñas, correlación score-longitud, palabras clave por rango de score (1-2, 3, 4-5).

2. **Pipeline ETL**: carga/validación → clasificación de emociones → enriquecimiento de datos → exportación Parquet.

3. **Validación de resultados**: emociones vs. sentimientos previos, correlación con `review_score`, validación manual de ~200 reseñas, visualizaciones e insights accionables.

---

## 👥 Beneficiarios

- **Gerentes de Producto** → priorizan mejoras en características que generan frustración
- **Equipo de Marketing** → destacan aspectos de confianza en campañas
- **Vendedores en Amazon** → identifican productos que necesitan reposicionamiento urgente