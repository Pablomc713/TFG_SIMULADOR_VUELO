# README — Plataforma de simulación de vuelo para apoyo docente

## 1. Descripción general del proyecto

Este repositorio contiene la documentación técnica y los archivos de configuración asociados al Trabajo Fin de Grado titulado:

**Diseño y validación de una plataforma de simulación de vuelo de bajo coste para apoyo docente en Ingeniería Aeroespacial**

El proyecto desarrolla una plataforma de simulación basada en **FlightGear**, orientada a su uso como herramienta de apoyo docente en asignaturas relacionadas con Mecánica de Vuelo, tratando conceptos como estabilidad, control, actuaciones e instrumentación aeronáutica.

El objetivo principal del sistema no es proporcionar un simulador certificado ni una réplica profesional de una cabina de vuelo, sino configurar un entorno docente accesible, reproducible y modificable, que permita relacionar conceptos teóricos con el comportamiento observable de una aeronave simulada.

La plataforma se apoya en tres elementos principales:

* el simulador de vuelo **FlightGear**;
* modelos de vuelo modificables, principalmente basados en **JSBSim** y, de forma complementaria, en **YASim**;
* hardware comercial de simulación, incluyendo plataforma informática, sistema de visualización y dispositivos físicos de control.

## 2. Finalidad del README

Este documento es una guía rápida de orientación dentro del repositorio. Su función es permitir identificar qué hay en cada carpeta, acceder directamente a la documentación, y arrancar el sistema en su configuración más básica.

**Para el procedimiento completo de instalación, configuración, verificación, resolución de incidencias y uso docente, consultar la [Guía de Usuario](ANEXOS/UCLM_EIIA_TFG_GUIA_USUARIO.pdf).** Ese documento desarrolla en detalle todo lo que aquí solo se enuncia.

## 3. Software utilizado

* **FlightGear Flight Simulator** — versión **2024.1.4**
* Sistema operativo de trabajo: **Windows**
* Motores de dinámica de vuelo analizados: **JSBSim** (principal) y **YASim** (comparativo)
* Herramientas internas empleadas: **Property Browser**, **Property Tree**, **Nasal Console**, archivos de configuración **XML**

## 4. Hardware utilizado

Hardware comercial de coste contenido, compatible con un entorno universitario: equipo informático con capacidad gráfica suficiente, sistema de visualización multimonitor, y dispositivos físicos de control de vuelo. La configuración concreta puede variar según el equipo disponible en el laboratorio.

Especificaciones de referencia utilizadas durante el desarrollo: procesador de arquitectura reciente, tarjeta gráfica dedicada, 32 GB de RAM, almacenamiento SSD.

## 5. Documentación del proyecto

Toda la documentación generada durante el desarrollo del TFG está disponible directamente en este repositorio:

* [**Memoria del TFG**](MEMORIA/UCLM_EIIA_TFG_2425_Pablo_Martín_Calzada_Mark_VII.pdf) — documento principal del Trabajo Fin de Grado.
* [**Guía de Usuario**](ANEXOS/UCLM_EIIA_TFG_GUIA_USUARIO.pdf) — instalación, configuración y puesta en marcha de la plataforma.
* [**Archivos Modificados de las Aeronaves**](ANEXOS/UCLM_EIIA_TFG_ARCHIVOS_MODIFICADOS_AERONAVES.pdf) — detalle de los archivos XML modificados en cada aeronave.
* [**Registro de desarrollo**](ANEXOS/UCLM_EIIA_TFG_REGISTRO_DESARROLLO.pdf) — seguimiento de sesiones de trabajo e incidencias.
* [**Estructura interna de FlightGear**](ANEXOS/UCLM_EIIA_TFG_INFORME_ESTRUCTURA_INTERNA_SW_FLIGHTGEAR.pdf) — informe técnico elaborado en la fase de análisis.
* [**Guion de prácticas — Cessna 172P**](GUIONES_PRACTICAS/UCLM_EIIA_TFG_GUION_CESSNA.pdf)
* [**Guion de prácticas — F-16**](GUIONES_PRACTICAS/UCLM_EIIA_TFG_GUION_F16.pdf)

Los archivos XML modificados, descritos en detalle en el anexo *Archivos Modificados de las Aeronaves*, están disponibles directamente en la carpeta `CODIGOS_MODIFICADOS/`:

* [**c172p_TFG.xml**](CODIGOS_MODIFICADOS/c172p_TFG.xml) — modelo aerodinámico de la Cessna 172P.
* [**F100-PW-200_TFG.xml**](CODIGOS_MODIFICADOS/F100-PW-200_TFG.xml) — modelo propulsivo del F-16 Block 10.
* [**jsb-aerodynamics-block1_TFG.xml**](CODIGOS_MODIFICADOS/jsb-aerodynamics-block1_TFG.xml) — aerodinámica del F-16 Block 10.
* [**jsb-controls_TFG.xml**](CODIGOS_MODIFICADOS/jsb-controls_TFG.xml) — sistema de control *fly-by-wire* del F-16 Block 10.

El sistema de visualización multimonitor finalmente empleado se configura mediante [**surround.xml**](CONFIG/surround.xml) (pantalla combinada NVIDIA Surround). La configuración experimental del sistema multicámara con frustum, documentada como línea de mejora futura, está en [**multiscreen_frustum.xml**](CONFIG/multiscreen_frustum.xml).

## 6. Estructura del repositorio

```text
.
├── README.md
│
├── MEMORIA/
│   └── UCLM_EIIA_TFG_2425_Pablo_Martín_Calzada_Mark_VII.pdf
│
├── ANEXOS/
│   ├── UCLM_EIIA_TFG_GUIA_USUARIO.pdf
│   ├── UCLM_EIIA_TFG_ARCHIVOS_MODIFICADOS_AERONAVES.pdf
│   ├── UCLM_EIIA_TFG_REGISTRO_DESARROLLO.pdf
│   └── UCLM_EIIA_TFG_INFORME_ESTRUCTURA_INTERNA_SW_FLIGHTGEAR.pdf
│
├── GUIONES_PRACTICAS/
│   ├── UCLM_EIIA_TFG_GUION_CESSNA.pdf
│   └── UCLM_EIIA_TFG_GUION_F16.pdf
│
├── CODIGOS_MODIFICADOS/
│   ├── c172p_TFG.xml
│   ├── F100-PW-200_TFG.xml
│   ├── jsb-aerodynamics-block1_TFG.xml
│   └── jsb-controls_TFG.xml
│
└── CONFIG/
    ├── surround.xml
    └── multiscreen_frustum.xml
```

`CODIGOS_MODIFICADOS/` contiene los archivos XML reales modificados durante el desarrollo de las prácticas, documentados en detalle en el anexo *Archivos Modificados de las Aeronaves*. `CONFIG/` recoge los archivos de configuración del sistema de visualización multimonitor: `surround.xml` es la configuración base finalmente empleada para el desarrollo y validación del proyecto (pantalla combinada mediante NVIDIA Surround, 5760×1080); `multiscreen_frustum.xml` corresponde a la configuración experimental del sistema multicámara con proyección geométrica por frustum, documentada en la memoria como línea de mejora futura.

Para la estructura de carpetas recomendada **dentro de la instalación de FlightGear** en el equipo del laboratorio (no del repositorio), consultar la sección siguiente.

## 7. Estructura recomendada en el equipo de laboratorio

```text
FlightGear\
│
├── Custom Aircraft\
│   ├── Cessna172P\
│   ├── F-16\
│   └── TecnamP92\
│
├── Config\
│   ├── multiscreen\
│   ├── launch\
│   └── controls\
│
├── Logs\
│   └── datos_simulacion\
│
└── Scripts\
    └── nasal\
```

Esta estructura puede adaptarse a la organización real del equipo o del laboratorio. Lo importante es mantener separadas las aeronaves modificadas, los archivos de configuración y los registros de datos.

## 8. Carpetas principales del equipo de laboratorio

* **`Custom Aircraft\`** — Aeronaves utilizadas: **Cessna 172P** (base de las prácticas convencionales: pérdida, estabilidad longitudinal, amortiguamiento, autoridad del elevador), **F-16** (base de las prácticas de altas prestaciones: régimen transónico, factor de carga, maniobra, control *fly-by-wire*) y **Tecnam P92** (caso comparativo basado en YASim, no usado como base de guiones docentes).
* **`Config\`** — Archivos auxiliares de arranque, visualización multimonitor y configuración de mandos.
* **`Logs\`** — Registros de simulación o datos exportados, preferiblemente en formato CSV.
* **`Scripts\`** — Scripts Nasal auxiliares empleados durante el desarrollo.

## 9. Aeronaves y modelos de vuelo

**JSBSim** se ha seleccionado como base principal de las prácticas docentes por su trazabilidad directa entre archivos XML, coeficientes aerodinámicos, masas, inercias y comportamiento observable. **YASim** se ha estudiado de forma comparativa mediante el Tecnam P92, como ejemplo de motor basado en descripción geométrica frente al enfoque tabular de JSBSim.

## 10. Puesta en marcha rápida

1. Verificar que FlightGear 2024.1.4 está instalado.
2. Comprobar que la ruta de aeronaves personalizadas está configurada en el Launcher.
3. Conectar los dispositivos físicos de control antes de abrir el simulador.
4. Seleccionar la aeronave y definir aeropuerto, pista y condiciones iniciales.
5. Iniciar la simulación y comprobar que los mandos responden.
6. Abrir el Property Browser para verificar que las variables internas son accesibles.

Ejemplo genérico de ejecución por línea de comandos:

```text
fgfs --aircraft=<nombre_aeronave> --airport=<codigo_icao> --runway=<pista>
```

Con archivo de configuración multimonitor:

```text
fgfs --config="ruta\al\archivo_surround.xml"
```

Las rutas y parámetros concretos deben adaptarse a la instalación de cada equipo. **El procedimiento detallado, paso a paso, con resolución de incidencias, está en la Guía de Usuario.**

## 11. Variables de interés

```text
/position/altitude-ft
/velocities/airspeed-kt
/orientation/pitch-deg
/orientation/roll-deg
/orientation/heading-deg
/controls/flight/elevator
/controls/flight/aileron
/controls/flight/rudder
/fdm/jsbsim/aero/alpha-deg
/fdm/jsbsim/aero/beta-deg
```

La disponibilidad exacta depende de la aeronave y del motor de dinámica de vuelo utilizado.

## 12. Modificación de archivos XML

Antes de modificar cualquier archivo: crear una copia de seguridad, cambiar un único parámetro cada vez, y comprobar el efecto en simulación antes de continuar. El procedimiento completo está descrito en la [Guía de Usuario](ANEXOS/UCLM_EIIA_TFG_GUIA_USUARIO.pdf), sección "Uso de archivos XML modificados". El detalle de qué archivos y funciones concretas se han modificado en cada aeronave, junto con los propios archivos XML reales, se recoge en [Archivos Modificados de las Aeronaves](ANEXOS/UCLM_EIIA_TFG_ARCHIVOS_MODIFICADOS_AERONAVES.pdf) y en la carpeta [`CODIGOS_MODIFICADOS/`](CODIGOS_MODIFICADOS/).

## 13. Estado actual y limitaciones

La plataforma no constituye un simulador certificado y no sustituye a ensayos reales de vuelo. La validación realizada hasta la fecha es **funcional y cualitativa**; las prácticas no han sido todavía aplicadas con alumnado real. Algunas configuraciones pueden depender del equipo utilizado y de la versión de FlightGear instalada.

**Tareas pendientes:** completar la Guía de Usuario, verificar todas las prácticas del F-16 en el simulador, trasladar los archivos modificados al equipo del laboratorio, integrar la estructura de cockpit adquirida, y validar el material docente en sesiones reales con alumnado.

## 14. Autor y tutor

**Autor:** Pablo Martín Calzada — Grado en Ingeniería Aeroespacial, Escuela de Ingeniería Industrial y Aeroespacial, Universidad de Castilla-La Mancha.

**Tutor:** Luis Sánchez Rodríguez.

## 15. Licencia y uso

Este material forma parte del Trabajo Fin de Grado indicado. Su uso está orientado a fines académicos, docentes y de documentación técnica del proyecto. Los nombres de programas, aeronaves, sistemas y productos mencionados pertenecen a sus respectivos propietarios y se citan únicamente con finalidad descriptiva y educativa.
