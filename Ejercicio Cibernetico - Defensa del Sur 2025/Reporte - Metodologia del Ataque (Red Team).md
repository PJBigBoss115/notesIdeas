#### 🗓️ Día 1: Reconocimiento y Enumeración

- El equipo Red Team inició con una **fase de reconocimiento activa** mediante escaneo de red, identificando rangos IP activos, puertos abiertos y servicios vulnerables en las interfaces públicas.
- Se enfocaron en recolectar posibles **credenciales** usando técnicas de fuerza bruta y diccionarios, además de buscar archivos expuestos y configuraciones débiles.
- Se realizaron campañas de **phishing básico** para identificar usuarios vulnerables y obtener acceso inicial.
- Se observó un patrón de **tráfico sospechoso** asociado a escaneos masivos (nmap, enum4linux, etc.) y consultas a servicios vulnerables.
- Esta etapa se centró en la **recolección de información y posibles vectores de ataque**, sin compromisos graves todavía.
- Indicadores clave de esta fase:
    - Escaneos de red con herramientas como `nmap` y `masscan`.
    - Enumeración de servicios y búsqueda de vulnerabilidades conocidas (CVEs).
    - Envío de correos de phishing con enlaces maliciosos.

#### 🗓️ Día 2: Acceso Inicial y Movimiento Lateral

- Un usuario cayó en la campaña de phishing y accedió al sitio malicioso, lo que permitió al equipo Red Team **obtener credenciales válidas**.
- Accedieron a un servidor vulnerable expuesto en la DMZ e **inyectaron malware** que les permitió establecer un punto de persistencia.
- A través de este foothold, comenzaron a hacer **movimiento lateral** hacia otras máquinas dentro de la red interna.
- Intentaron **escalar privilegios** explotando vulnerabilidades locales, pero algunas técnicas no fueron exitosas.
- Aprovecharon **servicios desactualizados** y configuraciones inseguras para desplegar herramientas como Cobalt Strike y Metasploit.
- En esta fase, comenzaron a generar **tráfico interno anómalo**, conexiones entre zonas que normalmente no se comunican.
- Indicadores:
    - Accesos sospechosos desde la DMZ a la LAN interna.
    - Comunicación con servidores C2 (Command and Control).
    - Registros de escalamiento fallido y posterior explotación de servicios vulnerables.

#### 🗓️ Día 3: Dominio comprometido

- Una vez dentro de la red interna, realizaron un **mapeo completo de la infraestructura** y descubrieron un dominio con configuraciones débiles.
- Utilizaron **credenciales de bajo privilegio** para intentar accesos comunes, logrando comprometer una cuenta y luego escalar a control total del dominio.
- Accedieron a cuentas de servicios en la nube (posiblemente mal configuradas o sin MFA).
- Con acceso al dominio, iniciaron la **extracción de datos (data exfiltration)** y movimientos laterales automáticos.
- Se identificó uso de herramientas para obtener hashes de contraseñas (como Mimikatz).
- Indicadores:
    - Logins inusuales desde ubicaciones no autorizadas.
    - Reutilización de contraseñas.
    - Consultas masivas al Active Directory.

#### 🗓️ Día 4: Persistencia y Explotación

- Con acceso completo al dominio, crearon **nuevos usuarios y administradores falsos** para mantenerse dentro del sistema.
- Comenzaron a **instalar software de minería de criptomonedas**, ejecutándose en segundo plano en máquinas comprometidas.
- Se desplegaron cargas maliciosas como **ransomware simulado**, creación de tareas programadas, y modificación de configuraciones de escritorio.
- Se establecieron **backdoors y conexiones salientes** hacia servidores del Red Team, indicando una persistencia avanzada.
- Intentaron modificar el Active Directory y generar nuevas políticas para mantener el control.
- Se observó tráfico de **botnets**, aunque no con impacto destructivo, más bien para monitoreo y control remoto.
- Indicadores:
    - Creación de usuarios no autorizados.
    - Conexiones salientes a IPs externas inusuales.
    - Actividades sospechosas en el Task Scheduler.
    - Transferencia de archivos con extensión `.exe`, `.bat`, `.ps1`.

### Técnicas empleadas por el Red Team

- **Reconocimiento**: Nmap, DNS enum, SNMP scans.
- **Acceso inicial**: Phishing (correo con enlaces a payloads maliciosos).
- **Ejecución**: Scripts Powershell, malware.
- **Persistencia**: Tareas programadas, usuarios ocultos.
- **Movimiento lateral**: SMB, RDP, WinRM.
- **Exfiltración**: HTTP, DNS tunelling.
- **Comando y control (C2)**: Conexiones reversas con Netcat o herramientas como Cobalt Strike.

### Detalles adicionales del ataque

- Se logró **evadir herramientas de detección** en máquinas Windows usando técnicas de **bypass de antivirus** y ejecución sin escribir en disco (living off the land).
- El equipo Red Team usó herramientas **open source** y automatizadas, lo cual les dio velocidad y flexibilidad.
- Se centraron en atacar el **Active Directory**, reconociendo su valor estratégico como núcleo del entorno.
- Las credenciales fueron obtenidas inicialmente mediante phishing, luego **crearon sus propias** para ocultar su acceso.

### Recomendaciones Finales

1. **Nunca usar cuentas administrativas como cuentas diarias**.
2. **Implementar segmentación de red estricta**, especialmente entre DMZ e intranet.
3. **Reforzar las configuraciones del Active Directory**, aplicar el principio de privilegio mínimo.
4. **Monitorear constantemente tráfico inusual**, especialmente conexiones salientes a direcciones externas.
5. **Aplicar parches y actualizaciones** en todos los servicios y aplicaciones.
6. **Separar roles y cuentas** para administración y operación diaria.
7. **Implementar doble factor de autenticación (2FA)** en servicios críticos y cuentas con privilegios.