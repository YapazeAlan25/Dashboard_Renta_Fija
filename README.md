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
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/7bc0df05-1d4d-4aa9-bc0c-cbcd7ef619de" />


### 2. Instrumentos CER (Ajustados por Inflación)
Modelado de flujos de caja reales proyectando los datos del REM (Relevamiento de Expectativas de Mercado), calculando TIRs reales y paridades con altísima precisión.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/01edd34e-c5a6-49da-9125-b3a52adec524" />


### 3. Curva Dollar Linked
Análisis de instrumentos atados al tipo de cambio oficial, estructurando la devaluación esperada e integrando los retornos sintéticos.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/0efb0ddd-6e81-443e-98c1-08333dc0f6e3" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/518d5c1b-87e3-4c70-abf3-d3b4c5de2b4f" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/02e7f123-237d-4ff3-aef1-2928a71418fd" />


### 4. Banda Alta de los Dólares
Visualización y proyecciones de tipos de cambio financieros (CCL, MEP) y futuros de ROFEX, permitiendo identificar el costo de cobertura y las tasas implícitas.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/11d8b9a8-e689-4c23-bc24-9ae37c0f67da" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/6ace3cff-76a5-4905-9eed-1de42968de96" />


### 5. Bonos Soberanos Hard Dollar
Curva de rendimientos de los bonos Ley Local y Ley Extranjera (ALs / GDs). Análisis de paridades, sensibilidades y yields contra el riesgo país.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/6d58ce9b-41c0-4ee4-bd34-8f4478deef8b" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/7cf96352-e675-42c5-a1eb-cc47c04f5dda" />


### 6. Obligaciones Negociables (Corporativos)
Monitoreo del universo de deuda corporativa, evaluando el spread de crédito de las empresas argentinas contra la curva soberana.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/6367e4ba-36c9-46f3-a83e-b6ec9c49815f" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/1b945b37-68cf-45d7-8035-e1a1f5aabf4d" />


### 7. Cronograma de Flujos Hard Dollar
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/974f6a3b-8287-4224-bb02-4100598cfe9a" />


### 8. Inflation Breakeven (Detección de Arbitraje)
Matriz cruzada de rendimientos que expone la inflación implícita del mercado (Breakeven Inflation) al comparar la curva nominal (Pesos) vs la curva real (CER). Expone de manera visual y automatizada los desarbitrajes y oportunidades de entrada.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/cb3c1556-d47d-4502-9e4a-bc6502217cb9" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/751b8919-8030-4c9d-a67d-c7a67ca16ecd" />


### 9. Análisis de Margen de Seguridad & Sintético USD
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/4472f1ab-6250-404c-b44b-41a9558ff4b2" />


---

## 💡 Impacto y Casos de Uso

1.  **Reducción del tiempo de análisis:** Tareas de cálculo que en Excel tomaban más de 30 minutos diarios de limpieza de datos, ahora ocurren en **menos de 3 segundos** de manera automatizada.
2.  **Trade Execution Insights:** Las ineficiencias de corto plazo saltan a la vista antes de que el mercado las corrija gracias al tablero de Inflation Breakeven.
3.  **Robustez y Mantenibilidad:** Migrar de planillas de cálculo propensas a errores a un backend en Python aumentó la fiabilidad a nivel institucional.

---
📫 **Contacto:** [alan_yapaze2015@outlook.com.ar / (https://www.linkedin.com/in/alan-yapaze/]
