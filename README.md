# 🩺 Health Tech FHIR Lakehouse with Databricks · Arquitectura Medallion en Databricks

[🇬🇧 Read in English](#en) | [🇦🇷 Leer en Español](#es)

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)]([https://www.python.org/](https://www.python.org/))
[![Databricks](https://img.shields.io/badge/Databricks-Serverless-FF3621?style=flat&logo=databricks&logoColor=white)](https://www.databricks.com/)
[![Apache Spark](https://img.shields.io/badge/Apache_Spark-Delta_Lake-E25A1C?style=flat&logo=apachespark&logoColor=white)](https://spark.apache.org/)
[![HL7 FHIR](https://img.shields.io/badge/Standard-HL7_FHIR-009688?style=flat&logo=hl7&logoColor=white)](https://www.hl7.org/fhir/)
[![Code: MIT](https://img.shields.io/badge/Code-MIT-green.svg)](LICENSE.md)
[![Status: Portfolio Project](https://img.shields.io/badge/Status-Data_Engineering_Portfolio-blue.svg)](#disclaimer--aviso)

---

<a id="en"></a>
## 🇬🇧 English Version

### 👥 Author
Horacio Bonafina

### 📌 Overview
End-to-end data engineering project implementing a **Medallion Architecture (Bronze, Silver, Gold)** on Databricks Serverless. The domain focuses on **Health Tech analytics using HL7 FHIR** (Fast Healthcare Interoperability Resources) synthetic datasets. 

The pipeline ingests raw healthcare transactions, cleans and structures them into relational silver tables, and aggregates key performance indicators (KPIs) and operational metrics in gold analytics tables to evaluate patient journeys, encounter durations, and clinical workflows.

### 🏆 Key Pipeline Stages
| Layer | Description | Storage Format | Objective |
|---|---|---|---|
| **Bronze** | Ingestion of raw health records / FHIR API responses | Delta Lake (Raw) | Immutable landing zone preserving raw historical data |
| **Silver** | Cleaning, schema enforcement, flattening, and relational transformation | Delta Lake (Cleaned) | Standardised, query-ready tables complying with data quality constraints |
| **Gold** | Business aggregations, patient KPIs, and analytical metrics | Delta Lake (Aggregated) | High-performance data marts for dashboards and reporting |

### 🧭 Methodology & Architecture
1. **Source:** Synthetic HL7 FHIR healthcare data simulating patients, encounters, observations, and conditions.
2. **Bronze Layer (`01_bronze_ingestion.ipynb`):** Automated ingestion of raw JSON payloads into Delta Lake tables, adding ingestion metadata (`_ingestion_timestamp`, `_source_system`).
3. **Silver Layer (`02_silver_transformation.ipynb`):** Parsing nested structures, flattening JSON fields, handling missing values, and enforcing relational integrity between patients and encounters.
4. **Gold Layer (`03_gold_analytics.ipynb`):** Building business-level aggregations (e.g., average length of stay, top conditions by frequency, patient demographics distribution) optimized for downstream consumption.
5. **Version Control & CI/CD:** Code organized following clean architecture principles inside Databricks Git folders and synchronized with GitHub.

### 📁 Project Structure
    ├── README.md
    ├── LICENSE.md
    ├── requirements.txt
    └── notebooks/
        ├── 01_bronze_ingestion.ipynb       # Raw ingestion and landing in Delta Lake
        ├── 02_silver_transformation.ipynb  # Relational cleaning, flattening, and standardisation
        └── 03_gold_analytics.ipynb         # Business KPIs, aggregations, and analytical reporting

### ▶️ How to Run
1. Clone this repository into your Databricks workspace using **Databricks Git Folders**.
2. Ensure you are running on a Databricks Serverless or standard Spark cluster.
3. Execute the notebooks sequentially:
   - Run `notebooks/01_bronze_ingestion.ipynb`
   - Run `notebooks/02_silver_transformation.ipynb`
   - Run `notebooks/03_gold_analytics.ipynb`

### 🔁 Reproducibility & Environment
Developed and tested on Databricks Serverless utilizing Apache Spark and Delta Lake abstractions. The modular structure allows seamless execution across different workspace environments or local development setups supporting PySpark.

### ⚠️ Limitations & Scope
Designed as a portfolio project showcasing Data Engineering patterns (Medallion architecture, Delta Lake, FHIR modeling). It utilizes synthetic datasets and does not process protected health information (PHI) or real patient records.

---

<a id="es"></a>
## 🇦🇷 Versión en Español

### 👥 Autor
Horacio Bonafina

### 📌 Descripción General
Proyecto integral de ingeniería de datos que implementa una **Arquitectura Medallion (Bronze, Silver, Gold)** sobre Databricks Serverless. El dominio del proyecto se centra en **analítica de salud utilizando datos sintéticos basados en el estándar HL7 FHIR** (Fast Healthcare Interoperability Resources).

El pipeline automatiza la ingesta de registros médicos crudos, realiza transformaciones relacionales y de limpieza en la capa intermedia, y consolida indicadores clave de rendimiento (KPIs) y métricas operativas en la capa gold para optimizar la visualización y análisis de flujos clínicos.

### 🏆 Fases Clave del Pipeline
| Capa | Descripción | Formato de Almacenamiento | Objetivo |
|---|---|---|---|
| **Bronze** | Ingesta de registros médicos crudos / respuestas de API FHIR | Delta Lake (Raw) | Zona de aterrizaje inmutable que preserva el dato original |
| **Silver** | Limpieza, aplicación de esquemas, aplanamiento y transformación relacional | Delta Lake (Cleaned) | Tablas estandarizadas y listas para consultas relacionales |
| **Gold** | Agregaciones de negocio, KPIs de pacientes y métricas analíticas | Delta Lake (Aggregated) | Modelos analíticos optimizados para reportes y tableros |

### 🧭 Metodología y Arquitectura
1. **Fuente:** Datos sintéticos en formato HL7 FHIR que simulan pacientes, encuentros clínicos, observaciones y diagnósticos.
2. **Capa Bronze (`01_bronze_ingestion.ipynb`):** Ingesta automatizada de payloads JSON crudos hacia tablas Delta, añadiendo metadatos de auditoría (`_ingestion_timestamp`, `_source_system`).
3. **Capa Silver (`02_silver_transformation.ipynb`):** Parseo de estructuras anidadas, aplanamiento de campos, gestión de nulos y garantía de integridad relacional entre pacientes y eventos médicos.
4. **Capa Gold (`03_gold_analytics.ipynb`):** Generación de métricas de negocio agregadas (ej. duración promedio de internación, patologías más frecuentes, distribución demográfica) para consumo analítico.
5. **Control de Versiones:** Código estructurado bajo principios de arquitectura limpia en subcarpetas dedicadas y sincronizado mediante integración continua con GitHub.

### 📁 Estructura del Proyecto
    ├── README.md
    ├── LICENSE.md
    ├── requirements.txt
    └── notebooks/
        ├── 01_bronze_ingestion.ipynb       # Ingesta cruda y almacenamiento en Delta Lake
        ├── 02_silver_transformation.ipynb  # Limpieza relacional, aplanamiento y estandarización
        └── 03_gold_analytics.ipynb         # KPIs de negocio, agregaciones y reportes analíticos

### ▶️ Cómo Ejecutarlo
1. Clona este repositorio en tu workspace de Databricks utilizando **Databricks Git Folders**.
2. Configura tu entorno con un cluster Databricks Serverless o un cluster Spark estándar.
3. Ejecuta los notebooks en orden secuencial:
   - Ejecutar `notebooks/01_bronze_ingestion.ipynb`
   - Ejecutar `notebooks/02_silver_transformation.ipynb`
   - Ejecutar `notebooks/03_gold_analytics.ipynb`

### 🔁 Reproducibilidad y Entorno
Desarrollado y probado sobre Databricks Serverless utilizando Apache Spark y Delta Lake. La estructura modular permite su ejecución fluida en cualquier workspace compatible con PySpark.

### ⚠️ Limitaciones y Alcance
Proyecto de portafolio orientado a demostrar patrones de Ingeniería de Datos (arquitectura Medallion, Delta Lake, modelado FHIR). Utiliza datos sintéticos y no procesa información de salud protegida (PHI) ni registros médicos reales.

---

<a id="disclaimer--aviso"></a>
## ⚕️ Disclaimer · Aviso
**🇬🇧** Portfolio project for Data Engineering, Databricks, and healthcare data modeling. It does not handle real clinical data or constitute a certified medical software product.

**🇦🇷** Proyecto de portafolio para Ingeniería de Datos, Databricks y modelado de datos de salud. No procesa datos clínicos reales ni constituye un producto de software médico certificado.
