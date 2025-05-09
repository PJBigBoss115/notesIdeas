### Hallazgo: Sincronización entre pares de BitTorrent ET P2P
>**HORA:** *2025-05-03 13:05:50.109 -04:00*

**IP DE ORGIGEN:** 192.168.16.81
**IP DE DESTINO:** 192.168.15.91, 192.168.15.205

**PUERTO DE ORIGEN:** 49907, 50142
**PUERTO DE DESTINO:** 7680

**PROTOCOLO:** TCP

#### **ALERTA:** ALTA
**RESUMEN:** Esta regla detecta la comunicación peer-to-peer (P2P) relacionada con BitTorrent, identificando específicamente un mensaje de sincronización entre pares de BitTorrent. Se activa con el tráfico TCP saliente desde una red doméstica a redes externas, excepto el tráfico en el puerto 7680, y busca una secuencia específica de bytes dentro de los primeros seis bytes de la carga útil del paquete. La alerta se activa cuando la secuencia detectada coincide con el patrón predefinido, dentro de un umbral determinado para evitar alertas excesivas. BitTorrent es un protocolo de intercambio de archivos ampliamente utilizado que permite distribuir archivos entre una red de pares.

### Hallazgo: ET P2P MS WUDO Sincronización entre Pares
>**HORA:** *2025-05-03 13:05:46.934 -04:00*

**IP DE ORGIGEN:** 192.168.16.81
**IP DE DESTINO:** 192.168.15.51

**PUERTO DE ORIGEN:** 7680
**PUERTO DE DESTINO:** 60090

**PROTOCOLO:** TCP

#### **ALERTA:** ALTA
**RESUMEN:** Esta regla detecta el tráfico relacionado con la sincronización entre pares de Windows Update Delivery Optimization (WUDO) de Microsoft a través de la red peer-to-peer (P2P). Se activa en conexiones TCP desde la red interna a hosts externos a través del puerto 7680 cuando se encuentra una secuencia de bytes específica, "|00 00 00 0d 06 00|",  dentro de los primeros 6 bytes de la carga útil. Este patrón de bytes indica el protocolo utilizado por WUDO, que ayuda a distribuir las actualizaciones de Windows de forma más eficiente mediante el intercambio de archivos peer-to-peer.