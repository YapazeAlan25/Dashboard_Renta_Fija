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
*   **Ultima Actualización:** Las imagenes adjuntadas aqui son correspondientes al cierre del 19/06/2026.
<div align="center">
  
</div>

---

## 📊 Módulos Principales y Demostraciones

El sistema está segmentado en módulos especializados que abarcan todo el espectro de la renta fija local:

### 1. Tasas en Pesos (Lecaps / Boncap)
El motor interpola las tasas del mercado en tiempo real, construye la curva cupón cero de pesos y proyecta retornos efectivos. 
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/eee04cb6-c8ab-4a31-8a6e-b14fa00f2da5" />


### 2. Instrumentos CER (Ajustados por Inflación)
Modelado de flujos de caja reales proyectando los datos del REM (Relevamiento de Expectativas de Mercado), calculando TIRs reales y paridades con altísima precisión.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/397705fc-ff33-47bc-b341-05a42feeb4bf" />


### 3. Curva Dollar Linked
Análisis de instrumentos atados al tipo de cambio oficial, estructurando la devaluación esperada e integrando los retornos sintéticos.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/b233063b-2977-4b41-8de5-6e181d99453b" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/226989c8-8608-4e93-ab18-41118c4ed1e8" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/8fdb75ef-98d9-4959-8112-8ed185f62074" />


### 4. Banda Alta de los Dólares
Visualización y proyecciones de tipos de cambio financieros (CCL, MEP) y futuros de ROFEX, permitiendo identificar el costo de cobertura y las tasas implícitas.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/d1dc1cf2-d0f0-42fc-8d7e-5fdc067199ed" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/3d5d22e6-e82a-482d-9bb2-1596554cfc9f" />


### 5. Bonos Soberanos Hard Dollar
Curva de rendimientos de los bonos Ley Local y Ley Extranjera (ALs / GDs). Análisis de paridades, sensibilidades y yields contra el riesgo país.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/f621de56-8e51-4c02-bfd2-60e9a9e98221" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/2d9c6711-01d3-4aca-9f32-b60e6ddec7c5" />


### 6. Obligaciones Negociables (Corporativos)
Monitoreo del universo de deuda corporativa, evaluando el spread de crédito de las empresas argentinas contra la curva soberana.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/5b3759f2-c223-4aca-87b2-5b57f040bc52" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/4df4212f-82db-4528-8368-9e4e9e7ad77e" />


### 7. Cronograma de Flujos Hard Dollar
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/77d9fa16-232e-44f6-b6eb-b9976827bd1d" />


### 8. Inflation Breakeven (Detección de Arbitraje)
Matriz cruzada de rendimientos que expone la inflación implícita del mercado (Breakeven Inflation) al comparar la curva nominal (Pesos) vs la curva real (CER). Expone de manera visual y automatizada los desarbitrajes y oportunidades de entrada.
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/03a375ec-868c-4ce1-bbf4-4b0eeaeb1f93" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/81f3cee4-8e92-470a-afb0-45ee9ffa82a6" />


### 9. Análisis de Margen de Seguridad & Sintético USD
> <img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/192f3786-6f0c-41b2-b6f6-84b21ed5d94f" />
<img width="3440" height="1392" alt="image" src="https://github.com/user-attachments/assets/37efadc2-103d-4b77-b51b-2261d521055e" />



---

## 💡 Impacto y Casos de Uso

1.  **Reducción del tiempo de análisis:** Tareas de cálculo que en Excel tomaban más de 30 minutos diarios de limpieza de datos, ahora ocurren en **menos de 3 segundos** de manera automatizada.
2.  **Trade Execution Insights:** Las ineficiencias de corto plazo saltan a la vista antes de que el mercado las corrija gracias al tablero de Inflation Breakeven.
3.  **Robustez y Mantenibilidad:** Migrar de planillas de cálculo propensas a errores a un backend en Python aumentó la fiabilidad a nivel institucional.

---
📫 **Contacto:** [alan_yapaze2015@outlook.com.ar / (https://www.linkedin.com/in/alan-yapaze/]
