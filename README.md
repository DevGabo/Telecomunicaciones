# 📊 Proyecto de Análisis de Clientes – ConnectaTel

## 🎯 Objetivo del Proyecto

El objetivo de este proyecto es analizar el comportamiento de los usuarios de ConnectaTel a partir de sus registros de uso (llamadas y mensajes) y su información demográfica, con el fin de:

- Identificar problemas de calidad de datos.
- Segmentar a los clientes según su nivel de uso y edad.
- Detectar patrones de consumo relevantes.
- Generar conclusiones accionables para la mejora de la oferta de planes comerciales.

---

## 🗂️ Datasets Utilizados

El análisis se basa en dos tablas principales:

### 1. `users`
Contiene la información demográfica y de suscripción de los clientes:

- `user_id`
- `first_name`
- `last_name`
- `age`
- `city`
- `reg_date`
- `plan`
- `churn_date`

### 2. `usage`
Contiene el registro de actividad de los usuarios:

- `id`
- `user_id`
- `type` (call / text)
- `duration` (para llamadas)
- `length` (para mensajes)
- `date`

### 3. `plans`
- `plan_name`
- `messages_included`
- `gb_per_month`
- `minutes_included`
- `usd_monthly_pay`
- `usd_per_gb`
- `usd_per_message`
- `usd_per_minute`


---

## 🧪 Etapas del Análisis Realizadas

### 1️⃣ Exploración y Calidad de Datos (EDA)

- Identificación de valores nulos y sentinels.
- Detección de fechas fuera de rango.
- Validación de coherencia entre columnas dependientes (`type` vs `duration/length`).
- Imputación de valores inválidos (edad, fechas).
- Tratamiento de la columna `city`.

### 2️⃣ Transformación y Limpieza

- Conversión de columnas a tipo fecha.
- Imputación de valores faltantes según contexto.
- Creación de variables auxiliares.
- Agregación de la tabla `usage` por `user_id`:
  - Cantidad de llamadas.
  - Cantidad de mensajes.
  - Total de minutos en llamadas.

### 3️⃣ Integración de Datos

- `merge` entre `users` y el resumen de `usage` para crear el dataframe `user_profile`.

### 4️⃣ Análisis Exploratorio y Visual

- Histogramas por plan.
- Boxplots y detección de outliers (método IQR).
- Análisis de distribución de uso y edad.

### 5️⃣ Segmentación de Clientes

Creación de nuevas variables:

- `grupo_uso` → Bajo uso, Uso medio, Alto uso.
- `grupo_edad` → Joven, Adulto, Adulto Mayor.

### 6️⃣ Insights Ejecutivos

- Identificación del segmento más valioso.
- Recomendaciones comerciales basadas en patrones reales de uso.

---

## 🔁 Guía de Reproducción

Para reproducir el análisis correctamente:

1. Cargar las librerías:
   - `pandas`
   - `numpy`
   - `matplotlib`
   - `seaborn`

2. Cargar los datasets:
   ```python
   users = pd.read_csv("users.csv")
   usage = pd.read_csv("usage.csv")
