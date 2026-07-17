# Robot Balancín Baymax: Control de Péndulo Invertido con Estética Futurista

## 👥 Colaboradores
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

<align="center">
  <img src="./Audiovisual/render_final.png" width="350" alt="Render del Robot Balancín Baymax">
  <img src="./Audiovisual/baymax_inspiration.png" width="280" alt="Inspiración Baymax">
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

## 📐 CAD (Diseño y Fabricación)
La carpeta [`/CAD`](./CAD) contiene los archivos de ingeniería necesarios para replicar la estructura del robot:
* **Modelos 3D:** Archivos nativos de Autodesk Fusion360 y formatos de intercambio estándar `.STEP` que integran el chasis en diagonal, soportes de motores y el mallado exterior de Baymax.
* **Planos 2D:** Archivos vectoriales (`.DXF` / `.SVG`) configurados para el proceso de corte láser de las placas base rígidas.

---

## 📦 BOM (Componentes y Materiales)
La carpeta [`/BOM`](./BOM) detalla la Lista de Materiales (Bill of Materials) del dispositivo. El diseño modular se optimizó distribuyendo los elementos en soportes compactos en diagonal para maximizar el uso del espacio interno:

| Componente / Material | Función Tecnológica | Criterio de Manufactura o Implementación |
| :--- | :--- | :--- |
| **Acrílico** | Chasis y placas estructurales planas. | Mecanizado mediante **Corte Láser**. |
| **PLA** | Soportes a medida y piezas externas estéticas. | Fabricado mediante **Impresión 3D (FDM)**. |
| **Sensor Giroscopio / Acelerómetro** | Unidad de Medición Inercial (IMU) para capturar la inclinación en tiempo real. | Montado de forma estrictamente **coplanar al soporte base** para mitigar errores de calibración. |
| **Motores DC** | Actuadores rotacionales dinámicos. | Encargados de corregir el par para recuperar el equilibrio. |
| **Controlador PID** | Microcontrolador (Placa compatible con Arduino). | Ejecución del bucle cerrado de control a alta frecuencia. |

---

## 💻 Código (Firmware y Control)
La carpeta [`/Codigo`](./Codigo) almacena el archivo principal `.ino` de firmware desarrollado para la plataforma. El algoritmo adquiere las lecturas cinemáticas de la IMU, calcula el error angular respecto a la vertical y ajusta el sentido de giro y ciclo de trabajo (PWM) de los motores.

### Parámetros sintonizados para el Controlador PID
Las constantes del controlador fueron determinadas inicialmente mediante el método de **Ziegler-Nichols** y refinadas posteriormente de forma iterativa en laboratorio:

* **Ganancia Proporcional ($K_p$):** `35`
* **Ganancia Integral ($K_i$):** `0.3`
* **Ganancia Derivativa ($K_d$):** `8`

---

## 🔌 Diagramas (Esquemas y Control Automático)
La carpeta [`/Diagramas`](./Diagramas) aloja la documentación circuital y el modelado sistémico del robot.

### Lógica de Ejecución y Lazo de Control
El sistema opera bajo una rutina cíclica cerrada que responde a variaciones angulares externas:

```mermaid
graph TD
    A[Calibración Inicial] --> B[Dejar en Libertad]
    B --> C[Lectura de Posición IMU]
    C --> D[Comparar Posición Actual vs Inicial]
    D --> E{¿Inclinado hacia adelante?}
    E -- Sí --> F[Motor gira en sentido contrario]
    E -- No --> G{¿Inclinado hacia atrás?}
    G -- Sí --> H[Motor gira en sentido contrario]
    F --> I{¿Volvió a la Posición Inicial?}
    H --> I
    G -- No --> I
    I -- No / Repetir --> C
    I -- Sí --> J[Detener / Estabilizado]
