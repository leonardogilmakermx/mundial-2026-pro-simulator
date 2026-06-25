# 🏆 World Cup 2026 - Simulator Pro v2.0.0
> **Tactical Analytics Center** | Híbrido Estocástico basado en el Modelo ELO + Simulación Montecarlo ($N=1000$) con Control de Restricción de Grafos.
--

## 📈 Resumen del Proyecto

Este simulador avanzado calcula las probabilidades probabilísticas de las 48 selecciones clasificadas para la Copa del Mundo 2026. A través de un motor estadístico de **Montecarlo de 1000 iteraciones**, el sistema modela el torneo completo desde la Fase de Grupos hasta la Gran Final, desplegando un árbol visual de eliminación directa simétrico (*Mirror Bracket*) y generando un ticket viral con métricas de rendimiento listas para compartir.

---

## 🚀 Novedades y Optimización (v2.0.0 Pro)

En esta segunda versión, se rediseñó por completo la arquitectura de datos para corregir el "congelamiento estadístico" y alinearse estrictamente a las normativas de competencia de la FIFA:

* **Algoritmo de Sanitización Radical de Llaves:** Se implementó un validador dinámico de procedencia basado en teoría de grafos. En la ronda de 16vos, el motor detecta colisiones y realiza intercambios (*swaps*) automáticos, garantizando que **ningún equipo del mismo grupo de origen se enfrente entre sí**, cumpliendo al 100% el reglamento de la FIFA.
* **Volatilidad Estocástica Escalonada (Factor Sorpresa):** Para romper la dominancia lineal del ELO estático, se introdujo ruido paramétrico Gaussiano en tres niveles de presión competitiva:
    * *Fase de Grupos:* $\pm 90$ puntos ELO (Permite empates y debacles lógicas).
    * *Fase KO Inicial:* $\pm 180$ puntos ELO (Representa el peso de la eliminación directa).
    * *Semis y Gran Final:* $\pm 300$ puntos ELO (Modela la tensión absoluta, tandas de penales y decisiones del VAR).
* **Calibración y Nivelación de la Élite (Ranking FIFA 2026):** Se actualizaron los ELOs base del Top 10 mundial para reflejar un ecosistema real y ultra competitivo, reduciendo la brecha entre potencias (Argentina, Francia, Inglaterra, España, Brasil) y ajustando a México con estatus de élite + un *Home Bias* balanceado de $+35$ puntos por su localía.
* **Corrección de Desborde en el Hilo de Ejecución:** Se reestructuró la matriz de siembra para asegurar vectores exactos de 16 nodos simétricos por rama en la ronda de 32, eliminando pérdidas silenciosas de datos en el renderizado de Plotly.

---

## 🛠️ Stack Tecnológico

* **Frontend Core:** HTML5, CSS3 (Variables nativas, diseño táctico futurista con efectos de desenfoque *backdrop-filter*).
* **Data Visualization:** [Plotly.js](https://plotly.com/javascript/) (Gráficas reactivas en tiempo real para análisis de avance y top de favoritos).
* **Image Processing:** [Html2canvas](https://html2canvas.hertzen.com/) (Renderizado del ticket de simulación en escala 2x con soporte CORS para descargas limpias).

---

## 📋 Arquitectura del Motor Estadístico

La probabilidad base de victoria entre dos selecciones se calcula mediante la curva logística estándar de la FIFA:

$$P(E_1) = \frac{1}{1 + 10^{\frac{R_2 - R_1}{400}}}$$

Donde:
* $R_1$ y $R_2$ representan los ELOs efectivos de los equipos, mutados dinámicamente en cada partido por las variables estocásticas de ruido Gaussiano individuales ($R_n + \Delta_{\text{Ronda}}$).
* Se aplica un modificador fijo de $R_n + 35$ si el equipo actúa como anfitrión administrativo en estadios norteamericanos.

---

## ✒️ Créditos y Desarrollo

* **Ingeniería de Software y Modelado Estadístico:** Ing. G. Leonardo Domínguez García.
* **Diseño Interfaz y Lógica del Bracket:** Tactical Analytics Center.
