## Actividades del 05 de mayo de 2025

**Objetivo:** Identificar hosts activos, servicios expuestos y posibles vectores de acceso utilizados por el Red Team.

## 🔍 Actividades Realizadas

### Tareas ejecutadas:

- Escaneo de red en múltiples segmentos internos.
- Revisión de puertos abiertos y servicios activos.
- Identificación de sistemas operativos y gateways por subred.
- Priorización de activos críticos y potenciales rutas de movimiento lateral.

### Segmentos evaluados:

- Admin: `192.168.16.64/27`
- DEV: `192.168.16.96/27`
- SecOnion Management: `192.168.58.0/27` <- Red Sensible no escanear
- SecOnion Access: `192.168.60.0/26` <- Red Sensible no escanear
- Red general: `192.168.30.0/24`

## Resultados del escaneo

### 🔸 **Admin – 192.168.16.64/27**

**Hosts detectados:** 4 activos / 31 posibles

|Dirección IP|Rol estimado|Puertos abiertos|Servicios detectados|Sistema Operativo|
|---|---|---|---|---|
|192.168.16.65|Gateway|22 (TCP)|SSH 7.9p1 (Debian 10)|Linux 3.1|
|192.168.16.66|Servidor|53 (TCP)|DNS sin identificar|Linux 3.2|
|192.168.16.67|Desconocido|53 (TCP)|DNS sin identificar|Linux 3.1|
|192.168.16.81|Cliente|22 (TCP)|SSH for_Windows_9.5|Windows 10 (1511)|

### 🔸 **DEV – 192.168.16.96/27**

**Hosts detectados:** 5 activos / 31 posibles

|Dirección IP|Rol estimado|Puertos abiertos|Servicios detectados|Sistema Operativo|
|---|---|---|---|---|
|192.168.16.97|Gateway|22 (TCP)|SSH 7.9p1 (Debian 10)|Linux 3.1|
|192.168.16.98|Servidor|53 (TCP)|DNS sin identificar|Linux 3.1|
|192.168.16.99|Servidor|53 (TCP)|DNS sin identificar|Linux 3.2 - 4.9|
|192.168.16.101|Cliente|2221 (TCP)|SSH 8.9p1 (Ubuntu)|Linux 3.2|
|192.168.16.102|Cliente|2222, 5710, 6610, 6611 (TCP)|SSH 8.9p1 (Ubuntu)|Linux 3.2|

## Observaciones Clave

- Algunos servidores presentan **puertos DNS (53) abiertos**, lo cual puede ser aprovechado para tunelización o exfiltración.
- Sistemas con **versiones antiguas de Linux** (3.x) podrían ser vulnerables a exploits conocidos (por ejemplo, _Dirty Cow_).
- **SSH sobre puertos no estándar (2221, 2222)** en DEV indica personalización intencional del sistema, posiblemente para evasión.
- El host Windows identificado (192.168.16.81) representa una superficie crítica por tener SSH expuesto en un entorno Windows.

## Recomendaciones Inmediatas

1. **Monitorear actividad SSH en puertos estándar y no estándar** (22, 2221, 2222).
2. **Revisar logs de DNS** en los servidores que corren este servicio para detectar posible uso malicioso.
3. **Aplicar parches de seguridad** en los sistemas con kernel Linux 3.x si no están actualizados.
4. **Segmentar acceso SSH** solo desde direcciones IP autorizadas.