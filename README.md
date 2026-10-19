<div align="center">

  # ⚽ La Liga 2015/16 Analytics: Tactical Usage Rate & Profiling
  ### *Análisis Multidimensional de Rendimiento: Neymar Jr. vs. Antoine Griezmann*

  [![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
  [![Pandas](https://img.shields.io/badge/Pandas-1.5%2B-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
  [![mplsoccer](https://img.shields.io/badge/mplsoccer-Latest-green?style=for-the-badge)](https://mplsoccer.readthedocs.io/)
  [![StatsBomb](https://img.shields.io/badge/Data-StatsBomb_Open_Data-red?style=for-the-badge)](https://statsbomb.com/resource-centre/statsbomb-open-data/)
  [![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

  [Descripción](#-descripción-del-proyecto) •
  [Metodología](#-metodología-y-cuota-de-uso) •
  [Métricas](#-pilares-de-evaluación) •
  [Instalación](#-instalación-y-uso) •
  [Resultados](#-resultados-clave) •
  [Créditos](#-créditos-y-fuentes)

</div>

---

## 📌 Descripción del Proyecto

Comparar futbolistas de elite que juegan en equipos con estilos tácticos opuestos (p. ej., un modelo de posesión dominante como el **FC Barcelona** frente a un bloque medio/bajo de transición rápida como el **Atlético de Madrid**) suele introducir sesgos severos al usar estadísticas absolutas.

Este proyecto resuelve ese problema mediante la implementación de la cuota de particiapción, contextualizando el volumen individual de acciones respecto a la actividad total del equipo. Se realiza un análisis comparativo profundo entre **Neymar Jr.** y **Antoine Griezmann** durante la temporada 2015/16 de La Liga utilizando datos de eventos (*event-level data*) de **StatsBomb**.

```
          ┌─────────────────────────────────────────────────────────┐
          │                  StatsBomb Open Data                    │
          └────────────────────────────┬────────────────────────────┘
                                       │
                                       ▼
          ┌─────────────────────────────────────────────────────────┐
          │          Data Pipeline & Feature Engineering            │
          │  - Ingesta de eventos por partido                       │
          │  - Normalización por porcentaje de participación        │
          │  - Agregación por Pilares (Ofensivo, Creador, etc.)     │
          └────────────────────────────┬────────────────────────────┘
                                       │
                                       ▼
          ┌─────────────────────────────────────────────────────────┐
          │             Profiling & PyPizza Visualization           │
          │         (Comparativa de Perfiles Multidimensional)      │
          └─────────────────────────────────────────────────────────┘
```

---

## 🔬 Metodología y Cuota de Uso

Para evitar el sesgo derivado del volumen de posesión global de cada equipo, se calcula la participación del jugador en relación con las acciones totales de su conjunto:

$$\text{Participación individual (\%)} = \left( \frac{\text{Acciones Totales del Jugador}}{\text{Acciones Totales del Equipo en los mismos partidos}} \right) \times 100$$

### Resultados de Normalización Táctica:
* **Neymar Jr. (FC Barcelona):** **`9.85%`** de participación individual en el sistema ofensivo culé.
* **Antoine Griezmann (Atlético de Madrid):** **`8.96%`** de participación individual en el esquema de Diego Simeone.

Esta métrica demuestra que, aunque el Barcelona acumula un volumen absoluto de pases y toques significativamente mayor, la participación individual de ambos jugadores dentro de sus estructuras tácticas es altamente equiparable.

---

## 📊 Pilares de Evaluación

El rendimiento se evalúa a través de 4 dimensiones principales agrupadas funcionalmente:

| Pilar | Métricas Evaluadas | Enfoque Analítico |
| :--- | :--- | :--- |
| **⚽ Ofensivo** | Goles sin penalti, $xG$ (Goles Esperados), Remates | Eficiencia rematadora y generación de peligro propio |
| **🎨 Creación** | Pases clave, $xA$ (Asistencias Esperadas), % Precisión | Generación de ocasiones y volumen de pase en último tercio |
| **⚡ Desborde** | Regates intentados, Regates con éxito, % Éxito | Capacidad de desequilibrio individual en 1v1 |
| **🛡️ Defensa** | Presiones aplicadas, Recuperaciones, Intercepciones | Aporte defensivo y volumen de trabajo sin balón |

---

## 📈 Resultados Clave

| Dimensión | Neymar Jr. (FC Barcelona) | Antoine Griezmann (Atlético Madrid) | Insight Táctico |
| :--- | :---: | :---: | :--- |
| **Rendimiento Goles / $xG$** | Alto volumen de $xG$ | Sobrerendimiento significativo vs $xG$ | Griezmann destaca por su altísima efectividad rematadora. |
| **Desborde (Regates)** | Dominio absoluto (>70% éxito) | Volumen moderado / funcional | Neymar es el principal generador de ventajas en 1v1. |
| **Trabajo Defensivo** | 392 Presiones | **619 Presiones** | Griezmann duplica el compromiso defensivo en bloque bajo. |
| **Cuota de Uso** | **9.85%** | **8.96%** | Participación estructural muy similar en sus respectivos equipos. |

---

## 🛠️ Tecnologías y Librerías

* **Lenguaje:** `Python 3.8+`
* **Procesamiento de Datos:** `pandas`, `numpy`
* **Visualización Avanzada:** `mplsoccer` (`PyPizza`), `matplotlib`
* **Extracción de Datos:** `statsbombpy`
* **Modelado Futuro:** `scikit-learn` (`NearestNeighbors` para similitud de perfiles)

---

## 🚀 Instalación y Uso

### 1. Clonar el repositorio
```bash
git clone https://github.com/tu-usuario/la-liga-2015-16-player-profiling.git
cd la-liga-2015-16-player-profiling
```

### 2. Crear entorno virtual (Recomendado)
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

### 3. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 4. Ejecutar el Notebook
```bash
jupyter notebook notebooks/player_profiling_la_liga.ipynb
```

---

## 📂 Estructura del Repositorio

```
la-liga-2015-16-player-profiling/
│
├── data/                       # Archivos locales de datos procesados (opcional)
├── notebooks/
│   └── player_profiling_la_liga.ipynb  # Notebook principal de Jupyter con el análisis
├── visuals/                    # Gráficas guardadas (Radares PyPizza, histogramas)
├── .gitignore                  # Exclusiones estándar de Git
├── LICENSE                     # Licencia del proyecto
├── README.md                   # Documentación del proyecto
```

---

## 🤝 Créditos y Fuentes

* **Datos:** Proveídos gratuitamente por **[StatsBomb Open Data](https://github.com/statsbomb/open-data)** para fines de investigación académica y analítica.
* **Visualizaciones:** Desarrolladas con **[mplsoccer](https://mplsoccer.readthedocs.io/)** (creado por Sergio Fonseca y Peter McKeever).

---

<div align="center">

Desarrollado con ❤️ para la comunidad de **Sports Analytics** & **Data Science**

</div>
