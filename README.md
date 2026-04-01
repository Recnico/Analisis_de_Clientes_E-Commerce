# 🐍 Pipeline de Análisis de Clientes E-Commerce — ABP Módulo 4

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

---

## 📌 Descripción del proyecto

Pipeline completo de obtención, integración, limpieza y análisis
de datos de clientes de una empresa de e-commerce, desarrollado
íntegramente en Python usando NumPy y Pandas.

El proyecto integra datos desde **4 fuentes distintas** (NumPy,
CSV, Excel y web), aplica técnicas de limpieza y wrangling, y
finaliza con segmentación de clientes y visualizaciones analíticas.

---

## 🎯 Objetivo

Construir un dataset consolidado y limpio a partir de múltiples
fuentes de datos, segmentar clientes por comportamiento de compra
e identificar patrones comerciales accionables.

---

## 🗂️ Fuentes de datos integradas

| Fuente | Descripción |
|---|---|
| 🔢 NumPy (.npy) | 100 transacciones generadas con distribución aleatoria |
| 📄 CSV local | 10 clientes con datos de compras reales |
| 📊 Excel local | Dataset complementario de clientes |
| 🌐 Web (GitHub) | Datos externos integrados via requests |

**Dataset final consolidado:** 110 registros · 8 columnas

---

## 🔧 Pipeline de trabajo

### Fase 1 — Generación y carga con NumPy
- Generación de 100 transacciones simuladas (IDs 1000–1099)
- Introducción intencional de outliers ($5.000 y $4.800)
- Cálculo de media, total y conteo de transacciones
- Exportación a formato `.npy`

### Fase 2 — Integración con Pandas
- Carga desde 4 fuentes: `.npy`, `.csv`, `.xlsx` y URL web
- Merge progresivo con `outer join` para no perder registros
- Consolidación de columnas duplicadas post-merge

### Fase 3 — Limpieza y calidad de datos
- Imputación de edad con mediana
- Relleno de valores categóricos nulos (`Ciudad`, `Nombre`)
- Reemplazo de montos en cero con mediana de montos reales
- Corrección de registros con compras sin monto asociado
- Eliminación de columnas irrelevantes

### Fase 4 — Detección de outliers
- Cálculo de IQR para identificar valores atípicos en `Monto_Total`
- Identificación de 2 outliers confirmados (transacciones > $3.700)

### Fase 5 — Feature engineering y segmentación
- Cálculo de `Venta_promedio` por cliente
- Segmentación en 3 categorías según monto total:

| Segmento | Criterio | Clientes |
|---|---|---|
| VIP | Monto > $3.000 | 5 |
| Activo | $1.000 – $3.000 | 5 |
| Estándar | Monto < $1.000 | 100 |

- Análisis agregado con `groupby`, `pivot_table` y `melt`

### Fase 6 — Visualización
- Gráfico de barras: ranking de ventas totales por segmento
- Boxplot: distribución y outliers del monto total

---

## 📈 Principales hallazgos

- El segmento **Estándar** lidera en volumen total de ingresos
  por cantidad: 100 clientes con montos bajos compensan con
  volumen de transacciones
- Los **5 clientes VIP** generan casi el mismo ingreso que los
  100 estándar, con una eficiencia por cliente muy superior
- El segmento **Activo** queda por debajo de ambos, representando
  una oportunidad de negocio para activación y upselling
- Se detectaron **2 outliers** con montos de $5.000 y $4.800,
  consistentes con el perfil VIP

---

## 🗂️ Estructura del repositorio

```
├── data/
│   ├── clientes_ecommerce.csv       # Dataset fuente CSV
│   ├── clientes_ecommerce.xlsx      # Dataset fuente Excel
│   ├── datos_iniciales.npy          # Datos NumPy generados
│   ├── dataframe_preliminar.csv     # Resultado fase 2
│   └── clientes_analisis_final.csv  # Dataset final limpio
├── notebooks/
│   └── ABP_Modulo4_Nicolas_Perez.ipynb  # Notebook principal
└── README.md
```

---

## 🛠️ Tecnologías utilizadas

| Librería | Uso |
|---|---|
| NumPy | Generación de datos y operaciones matriciales |
| Pandas | Carga, integración, limpieza y transformación |
| Matplotlib | Visualización base |
| Seaborn | Gráficos estadísticos (barplot, boxplot) |
| Requests + IO | Obtención de datos desde la web |

---

## 🚀 Cómo ejecutar

```bash
# Clonar el repositorio
git clone https://github.com/Recnico/Pipeline-Clientes-Ecommerce.git

# Instalar dependencias
pip install numpy pandas matplotlib seaborn openpyxl requests

# Abrir el notebook
jupyter notebook notebooks/ABP_Modulo4_Nicolas_Perez.ipynb
```

---

## 👤 Autor

**Nicolás Pérez Cerda**
[LinkedIn](https://www.linkedin.com/in/nicolasperezcerda/) · [GitHub](https://github.com/Recnico)
