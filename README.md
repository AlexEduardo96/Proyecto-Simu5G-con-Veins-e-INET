# 🚗📡 Red Heterogénea Vehicular con Dual Connectivity y D2D en Simu5G

Este repositorio contiene la modificación de escenarios base del simulador **Simu5G** para implementar una **red vehicular heterogénea** que combina:

- Conectividad dual LTE + 5G (Dual Connectivity)
- Vehículos móviles controlados por SUMO
- Comunicación directa entre vehículos (D2D)

## 📌 Objetivo

Diseñar un entorno de simulación vehicular donde los nodos móviles (vehículos) puedan:

- Recibir tráfico VoIP desde un servidor mediante doble conectividad (eNB + gNB).
- Comunicarse directamente entre sí mediante enlaces tipo D2D.
- Simular movilidad realista usando SUMO y Veins.

## ⚙️ Escenarios involucrados

- `DualConnectivity`: usado como base para la conexión simultánea a LTE y 5G.
- `cars`: usado como base para la movilidad vehicular gestionada por SUMO.

## 🛠️ Modificaciones realizadas

- Reemplazo del módulo UE por `NRCar[]` en el archivo `.ned`.
- Activación de `VeinsManager` y `VeinsInetMobility` en el `omnetpp.ini`.
- Creación del bloque `[Config DualConn-MasterPlusSecondary-DL]` con soporte para:
  - Tráfico VoIP desde servidor a cada vehículo.
  - Comunicación D2D entre `car[0]` y `car[1]`.

## 🧪 Resultados observados

- Los vehículos establecen conexión dual con eNB y gNB.
- Se recibe tráfico VoIP desde el servidor mediante ambas celdas.
- Se evidencia comunicación directa entre vehículos usando paquetes `LteMacPdu` (1 SDU, 0 CEs).
- **Conclusión:** la comunicación D2D está presente, pero no es `Sidelink (PC5)` puro. Las estaciones base siguen gestionando y participando en la transmisión.

## 📂 Estructura del repositorio

