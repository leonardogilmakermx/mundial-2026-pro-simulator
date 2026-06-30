# 🏆 World Cup 2026 - Simulator Pro v3.5.0
> **Tactical Analytics Center** | Motor Estadístico Híbrido: ELO Dinámico + Modelo de Simulación Montecarlo ($N=1000$) + Inyección Contextual Ambiental.

[![GitHub Pages](https://img.shields.io/badge/Deployment-GitHub%20Pages-00ffff?style=flat-square&logo=github)](https://leonardogilmakermx.github.io/mundial-2026-pro-simulator/)
[![License: MIT](https://img.shields.io/badge/License-MIT-d4af37.svg?style=flat-square)](https://opensource.org/licenses/MIT)

---

## 📈 Resumen del Proyecto

Este simulador de alto rendimiento procesa probabilísticamente el desenlace de la Copa del Mundo 2026. Computa análisis macro agregados mediante **1,000 iteraciones en bucles Montecarlo** para generar las tendencias de Plotly, y cuenta con un módulo de predicción micro calibrado con el **calendario y llaves reales en vivo de Google / ElEditor Platense**, calculando marcadores exactos, prórrogas y tandas de penales de forma cronológica.

---

## 🚀 Novedades de la Versión 3.5.0 (Módulo Contextual Activo)

La arquitectura del script evolucionó de un modelo puramente probabilístico a un entorno dinámico guiado por factores logísticos y ambientales reales:

* **Mapeo Fijo Reglamentario (Google / ElEditor Platense Data):** Se implementó una bifurcación lógica en el motor. Al accionar el módulo de pronóstico, el sistema bloquea los vectores exactos de los 32 clasificados reales (Rama Izquierda y Derecha simétricas: *Alemania vs Paraguay*, *Países Bajos vs Marruecos*, *México vs Ecuador*, etc.), simulando el camino unívoco hacia el título.
* **Vector de Contexto Ambiental (Física del Torneo):** Cada partido en fases eliminatorias calcula aleatoriamente una sede norteamericana oficial, cruzando metadatos geofísicos individuales:
    * **Factor Altitud:** Sedes elevadas (CDMX, Guadalajara) penalizan con $-45$ puntos de ELO transitorio a selecciones no habituadas a la hipoxia.
    * **Factor Clima (Estrés Térmico):** Sedes del sur en verano penalizan con $-30$ puntos de ELO a equipos sin adaptación al calor extremo y alta humedad.
* **Factor Forma y Ritmo Competitivo:** El motor KO hereda dinámicamente el rendimiento acumulado en fases previas, inyectando un modificador de $+10$ puntos ELO por cada punto obtenido en grupos y $+5$ puntos por balance en Diferencia de Goles (DG).
* **Sanitización Total del Ecosistema de Datos:** Se reestructuró la matriz base y el diccionario general (`db`), dando de alta e integrando de manera limpia a todas las naciones del fixture real (incluyendo *Austria, Bosnia y RD Congo*) con sus respectivas banderas ISO, previniendo excepciones por punteros vacíos (`undefined`).
* **Optimización del Hilo de Ejecución:** Se eliminaron redundancias y duplicaciones críticas de datos en los arrays de grupos, blindando el script contra bucles infinitos de permutación y estabilizando el renderizado reactivo de los gráficos de Plotly.

---

## 🛠️ Stack Tecnológico

* **Visualización Dinámica:** [Plotly.js](https://plotly.com/javascript/) (Análisis probabilístico de avance y Top 15 favoritos interactivo).
* **Renderizado de Interfaz:** HTML5 / CSS3 (Diseño táctico deportivo, modo oscuro stadium, grids responsivos y efectos de desenfoque por hardware con *backdrop-filter*).
* **Captura de Datos:** [Html2canvas](https://html2canvas.hertzen.com/) (Generador estático a escala 2x para descargas limpias de boletos predictivos con soporte CORS).

---

## 📋 Modelo Matemático del Motor

La probabilidad base se rige por la función de distribución logística acumulativa, mutada transitoriamente por los coeficientes de entorno:

$$P(E_1) = \frac{1}{1 + 10^{\frac{(R_2 + \Delta_{\text{Amb2}}) - (R_1 + \Delta_{\text{Amb1}} + \Delta_{\text{Forma}})}{400}}}$$

Donde el ruido blanco estocástico escala exponencialmente por ronda para simular la presión absoluta en tiempos extras y penales ($\pm 90$ en Grupos, $\pm 180$ en KO Inicial, $\pm 300$ en Semis/Final).

---

## ✒️ Créditos

* **Desarrollo de Software y Modelado Estocástico:** Ing. G. Leonardo Domínguez García.
* **Infraestructura de Datos:** Tactical Analytics Center.
