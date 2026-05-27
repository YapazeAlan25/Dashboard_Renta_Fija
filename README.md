<div align="center">

# 📈 Alpha Fixed Income: Quantitative Pricing & Arbitrage Engine

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg?style=for-the-badge&logo=python&logoColor=white)]()
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B.svg?style=for-the-badge&logo=Streamlit&logoColor=white)]()
[![DuckDB](https://img.shields.io/badge/DuckDB-FFF000.svg?style=for-the-badge&logo=duckdb&logoColor=black)]()
[![Docker](https://img.shields.io/badge/Docker-2496ED.svg?style=for-the-badge&logo=Docker&logoColor=white)]()
[![Status](https://img.shields.io/badge/Status-Private_Source-red.svg?style=for-the-badge)]()

*Un pipeline institucional de datos y motor de valuación en tiempo real para el mercado de Renta Fija Argentina.*

</div>

---

## 🚀 Resumen Ejecutivo

**Alpha Fixed Income** es una solución integral orientada a la toma de decisiones algorítmicas y visuales en el mercado financiero. Diseñado para analistas cuantitativos y portfolio managers, el sistema ingesta datos de múltiples fuentes (APIs bursátiles, BCRA), procesa curvas de rendimiento en tiempo real y detecta ineficiencias de mercado de manera automatizada.

> 🔒 **Nota sobre el Código Fuente:** 
> Debido a la naturaleza propietaria de los algoritmos de valuación y estrategias de arbitraje, **el código fuente de este proyecto se mantiene en un repositorio privado**. Este repositorio actúa como una *vidriera técnica* para ilustrar la arquitectura, capacidades y el impacto del sistema.

---

## 🏗️ Arquitectura del Sistema

El proyecto fue construido bajo estándares de ingeniería de software para escalabilidad y baja latencia, utilizando el siguiente stack:

*   **Data Ingestion & APIs:** Conectores asíncronos en Python para *InvertirOnline (IOL)*, *BCRA*, y web scrapers para mercados de futuros (ROFEX).
*   **Data Warehouse:** Almacenamiento columnar ultrarrápido con **DuckDB** y archivos **Parquet**, separando los datos en capas.
*   **Quantitative Models:** Pricers construidos desde cero con `NumPy` y `Pandas` para valuación de la curva entera de instrumentos argentinos.
*   **Interfaz de Usuario (UI):** Dashboard interactivo de grado institucional desarrollado en **Streamlit**.
*   **Infraestructura:** Todo el entorno está contenerizado utilizando **Docker** y orquestado con `docker-compose`.

<div align="center">
  
> *(Sugerencia: 🖼️ **[AQUÍ INSERTA UNA IMAGEN O DIAGRAMA SIMPLE DE TU ARQUITECTURA]**)*

</div>

---

## 📊 Módulos Principales y Demostraciones

El sistema está segmentado en módulos especializados que abarcan todo el espectro de la renta fija local:

### 1. Tasas en Pesos (Lecaps / Boncap)
El motor interpola las tasas del mercado en tiempo real, construye la curva cupón cero de pesos y proyecta retornos efectivos. 
> 🖼️ **[INSERTA AQUÍ UN GIF O CAPTURA DEL DASHBOARD DE TASA FIJA]**

### 2. Instrumentos CER (Ajustados por Inflación)
Modelado de flujos de caja reales proyectando los datos del REM (Relevamiento de Expectativas de Mercado), calculando TIRs reales y paridades con altísima precisión.
> 🖼️ **[INSERTA AQUÍ UNA CAPTURA DEL MÓDULO CER]**

### 3. Curva Dollar Linked
Análisis de instrumentos atados al tipo de cambio oficial, estructurando la devaluación esperada e integrando los retornos sintéticos.
> 🖼️ **[INSERTA AQUÍ UNA CAPTURA DEL MÓDULO DOLLAR LINKED]**

### 4. Banda Alta de los Dólares
Visualización y proyecciones de tipos de cambio financieros (CCL, MEP) y futuros de ROFEX, permitiendo identificar el costo de cobertura y las tasas implícitas.
> 🖼️ **[INSERTA AQUÍ UNA CAPTURA DEL MÓDULO DE BANDA ALTA]**

### 5. Bonos Soberanos Hard Dollar
Curva de rendimientos de los bonos Ley Local y Ley Extranjera (ALs / GDs). Análisis de paridades, sensibilidades y yields contra el riesgo país.
> 🖼️ **[INSERTA AQUÍ UNA CAPTURA DEL MÓDULO SOBERANOS USD]**

### 6. Obligaciones Negociables (Corporativos)
Monitoreo del universo de deuda corporativa, evaluando el spread de crédito de las empresas argentinas contra la curva soberana.
> 🖼️ **[INSERTA AQUÍ UNA CAPTURA DEL MÓDULO CORPORATIVOS]**

### 7. Inflation Breakeven (Detección de Arbitraje)
Matriz cruzada de rendimientos que expone la inflación implícita del mercado (Breakeven Inflation) al comparar la curva nominal (Pesos) vs la curva real (CER). Expone de manera visual y automatizada los desarbitrajes y oportunidades de entrada.
> 🖼️ **[INSERTA AQUÍ UNA CAPTURA DEL INFLATION BREAKEVEN]**

---

## 💡 Impacto y Casos de Uso

1.  **Reducción del tiempo de análisis:** Tareas de cálculo que en Excel tomaban más de 30 minutos diarios de limpieza de datos, ahora ocurren en **menos de 3 segundos** de manera automatizada.
2.  **Trade Execution Insights:** Las ineficiencias de corto plazo saltan a la vista antes de que el mercado las corrija gracias al tablero de Inflation Breakeven.
3.  **Robustez y Mantenibilidad:** Migrar de planillas de cálculo propensas a errores a un backend en Python aumentó la fiabilidad a nivel institucional.

---

## 👨‍💻 Sobre el Autor

Desarrollado combinando profundos conocimientos en **Finanzas Cuantitativas** e **Ingeniería de Datos y Software**. 

*Si sos reclutador, hiring manager o analista y deseas coordinar una entrevista técnica para ver una demostración del código en vivo y la lógica matemática/financiera detrás de los algoritmos de pricing, no dudes en contactarme.*

📫 **Contacto:** [Tu Email / Tu LinkedIn]
