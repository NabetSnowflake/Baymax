
# Robot Balancín Baymax: Control de Péndulo Invertido con Estética Futurista

## Integrantes
* **Ignacio Montero**
* **Ignacio Sanhueza**
* **Matias Yanine**
* **Rodrigo Pino**

* **Institución:** Universidad de Chile
* **Facultad:** Facultad de Ciencias Físicas y Matemáticas (FCFM)  
* **Departamento:** Departamento de Ingeniería Mecánica (DIMEC)
* **Laboratorio:** LEMUR (Laboratorio de Mecatrónica y Robótica)
* **Asignatura:** ME4250 Mecatrónica (Semestre 2025-2)

---

## Registro Visual del Prototipo

  <img width="350" height="320" alt="a1efa50e-f962-4aa4-a89f-e16bbc3a32e7" src="https://github.com/user-attachments/assets/3aa16ee2-ad40-4760-a161-078bc701e303" />
</align>

*Figura 1: Robot balancín inspirado en el personaje Baymax, de la película "Big Heroes".*

---

## Índice de Contenido

Este repositorio contiene la documentación técnica completa, archivos de fabricación y algoritmos que sustituyen al informe final del proyecto. La estructura se organiza de la siguiente manera:

1. [Descripción del Proyecto](#-descripción-del-proyecto)
2. [CAD (Diseño y Fabricación)](#-cad-diseño-y-fabricación)
3. [BOM (Componentes y Materiales)](#-bom-componentes-y-materiales)
4. [Código (Firmware y Control)](#-código-firmware-y-control)
5. [Diagramas (Esquemas y Control Automático)](#-diagramas-esquemas-y-control-automático)
6. [Audiovisual (Avances y Resultados)](#-audiovisual-avances-y-resultados)
7. [Referencias y Citas](#-referencias-y-citas)

---

## Descripción del Proyecto

Este proyecto consiste en el diseño, modelado, manufactura y programación de un **robot móvil de dos ruedas paralelas basado en el principio del péndulo invertido**. El robot debe poseer su centro de masa por encima del eje de tracción, por lo que se requiere el uso de un control PID para mantener un ángulo en torno al equilibrio inestable presente en la posición vertical. Además, se propuso el tema de un robot futurista, inspirado en el presonaje Baymax.

---

## CAD (Diseño y Fabricación)
La carpeta [`/CAD`](./CAD) contiene los archivos de ingeniería necesarios para replicar la estructura del robot:
* **Modelos 3D:** Archivos nativos de Autodesk Fusion360 y formatos de intercambio estándar `.STEP` que integran el chasis en diagonal, soportes de motores y el mallado exterior de Baymax.
* **Planos 2D:** Archivos vectoriales (`.DXF` / `.SVG`) configurados para el proceso de corte láser de las placas base rígidas.

