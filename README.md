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
*   **Ultima Actualización:** Las imagenes adjuntadas aqui son correspondientes al cierre del 27/05/2026.
<div align="center">
  
</div>

---

## 📊 Módulos Principales y Demostraciones

El sistema está segmentado en módulos especializados que abarcan todo el espectro de la renta fija local:

### 1. Tasas en Pesos (Lecaps / Boncap)
El motor interpola las tasas del mercado en tiempo real, construye la curva cupón cero de pesos y proyecta retornos efectivos. 
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/59fe1983-fc6a-4252-8264-4812a0f1a020" />

### 2. Instrumentos CER (Ajustados por Inflación)
Modelado de flujos de caja reales proyectando los datos del REM (Relevamiento de Expectativas de Mercado), calculando TIRs reales y paridades con altísima precisión.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/5d5ce6f3-826e-434a-bd17-fd9aed672647" />

### 3. Curva Dollar Linked
Análisis de instrumentos atados al tipo de cambio oficial, estructurando la devaluación esperada e integrando los retornos sintéticos.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/304fd816-27a6-487a-b891-346c0ed6a3a3" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/6bb5fee9-ce61-4263-b3a9-17f255c6c40d" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/ec349bf3-8a55-47f5-b954-2d9277713454" />

### 4. Banda Alta de los Dólares
Visualización y proyecciones de tipos de cambio financieros (CCL, MEP) y futuros de ROFEX, permitiendo identificar el costo de cobertura y las tasas implícitas.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/382c5f93-03a5-4e11-83e0-2ba39436a6de" />

### 5. Bonos Soberanos Hard Dollar
Curva de rendimientos de los bonos Ley Local y Ley Extranjera (ALs / GDs). Análisis de paridades, sensibilidades y yields contra el riesgo país.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/42ad5b6f-0bc3-48c7-93f9-89472a26328d" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/a71dd1bf-2cc3-46b3-b4e4-6236d228447b" />

### 6. Obligaciones Negociables (Corporativos)
Monitoreo del universo de deuda corporativa, evaluando el spread de crédito de las empresas argentinas contra la curva soberana.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/841b72ab-cff3-49ff-9cbb-0faa73501eb6" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/5b5b4f35-b580-4b08-9fd9-0f22dc22770e" />

### 7. Inflation Breakeven (Detección de Arbitraje)
Matriz cruzada de rendimientos que expone la inflación implícita del mercado (Breakeven Inflation) al comparar la curva nominal (Pesos) vs la curva real (CER). Expone de manera visual y automatizada los desarbitrajes y oportunidades de entrada.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/0a2bdeb1-2443-487e-b26c-afa0936064b6" />

---

## 💡 Impacto y Casos de Uso

1.  **Reducción del tiempo de análisis:** Tareas de cálculo que en Excel tomaban más de 30 minutos diarios de limpieza de datos, ahora ocurren en **menos de 3 segundos** de manera automatizada.
2.  **Trade Execution Insights:** Las ineficiencias de corto plazo saltan a la vista antes de que el mercado las corrija gracias al tablero de Inflation Breakeven.
3.  **Robustez y Mantenibilidad:** Migrar de planillas de cálculo propensas a errores a un backend en Python aumentó la fiabilidad a nivel institucional.

---
📫 **Contacto:** [Tu Email / Tu LinkedIn]
