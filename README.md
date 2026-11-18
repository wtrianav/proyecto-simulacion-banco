# Actividad Didáctica 2 - Simulación de Sistema Bancario (Módulo 3)

## Descripción del Proyecto
Este repositorio contiene la solución a la "Actividad didáctica 2 - M3", enfocada en el modelado y simulación de colas para optimizar la atención al cliente en una sucursal del Banco de Colombia. 

El objetivo principal es determinar la distribución óptima de 3 cajas de atención humana, decidiendo si se deben asignar dos cajas para retiros y una para pagos, o viceversa. El sistema se modela como colas M/M/1 independientes utilizando eventos discretos.

Se evaluaron dos escenarios simulando jornadas de 8 horas con 10 réplicas cada uno:
*   **Modelo 1:** 2 cajeros exclusivos para Retiros y 1 cajero para Consignaciones/Pagos.
*   **Modelo 2:** 1 cajero exclusivo para Retiros y 2 cajeros para Consignaciones/Pagos.

## Requisitos Previos
Para ejecutar esta simulación, necesitas tener instalado Python 3.x junto con las siguientes librerías:
*   `simpy` (para la simulación de eventos discretos)
*   `pandas` (para la visualización de las tablas de datos)
*   `numpy` (para los cálculos estadísticos de los promedios)

## Instrucciones de Instalación y Ejecución

1. Clona este repositorio o descarga los archivos en tu máquina local.
2. Abre una terminal o consola de comandos en la ruta de la carpeta del proyecto.
3. Instala las dependencias necesarias ejecutando el siguiente comando:
   ```bash
   pip install simpy pandas numpy
   ```
4. Ejecuta el script principal de la simulación:
   ```bash
   python simulacion_banco.py
   ```
*(Nota: El código también es totalmente compatible con entornos de ejecución como Jupyter Notebook dentro de Visual Studio Code).*

## Evidencias y Conclusiones de los Resultados

Tras ejecutar las 10 réplicas de la simulación en el script, se obtuvieron las siguientes métricas y conclusiones clave:

1. **Tiempos Promedio de Atención:**
   * **Retiros:** ~1.96 minutos (Cajero más rápido).
   * **Pagos/Consignaciones:** ~3.89 minutos (Cajero más lento, influenciado fuertemente por los usuarios "Muy lentos").

2. **Tiempos de Espera y Distribución de Cajeros:**
   * **Modelo 1 (2 Retiros, 1 Pago):** Los tiempos de espera colapsan en los pagos, alcanzando promedios de 206.58 minutos.
   * **Modelo 2 (1 Retiro, 2 Pagos):** Esta distribución resulta ser más equilibrada para los recursos humanos actuales. Al destinar 2 cajas a los pagos, el tiempo de espera de esta área se reduce a 172.02 minutos, absorbiendo mejor el cuello de botella. **Esta es la configuración sugerida.**

3. **Necesidad de Cajeros Electrónicos:**
   * Analizando los tiempos de espera promedio (que superan las 2 y 3 horas en ambos modelos), se concluye que **es estrictamente necesario implementar al menos un cajero electrónico** dedicado a los retiros. Esto mitigará la saturación y permitirá al personal humano enfocarse en las transacciones complejas de pagos y consignaciones.