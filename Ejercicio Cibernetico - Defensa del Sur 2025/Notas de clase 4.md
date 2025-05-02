### **Leyes y tratados internacionales en ciberseguridad**

- **Cada Estado tiene la obligación de actuar conforme a normas internacionales.**
- Las leyes ayudan a **organizar** y **responder** ante conflictos, especialmente en el ámbito digital.
- Cuando hablamos de **leyes de conflicto**, se hace referencia a las **acciones que pueden desencadenar una guerra o ciberataque**, y cómo se justifica la defensa.
- La **ley de subsidiariedad** implica que las acciones deben tomarse a nivel local primero antes de escalar a niveles internacionales o superiores.

> 📌 _Nota aclaratoria_: Se destacó la **necesidad de tener leyes específicas para ciberseguridad**. Sin un marco legal, no se puede actuar efectivamente ante un ciberataque, sobre todo si proviene de otro país. Esto genera una "zona gris" legal.

**Ejemplos tratados mencionados:**

- Budapest Convention (sobre delitos informáticos)
- Marco de trabajo de la ONU sobre ciberseguridad
- Casos reales y menciones a series como _Zero Day_ (ejemplo de cómo se refleja en medios).

> ❓ **¿Dónde están las fronteras en el ciberespacio?** Difícil de definir: una acción digital puede cruzar “fronteras” sin intención clara.

---

### **Análisis de puertos con Nmap**

#### Ejemplo de escaneo:

- **Puerto abierto**: `22/tcp (SSH)`

    - **Servicio**: OpenSSH 7.9p1 Debian
    - **Protocolo**: SSH 2.0
    - **TTL**: 1 (probablemente misma red/subred)
    - **Uptime**: ~20 días (último reinicio 8 abril 2025)

#### Interpretación:

- Si el puerto está **abierto**, hay un servicio activo.
- Si está **cerrado**, no hay nada escuchando pero el host está activo.
- Si está **filtrado**, probablemente hay un **firewall** bloqueando el acceso.

###  **Wireshark: análisis de red**

- Es un **analizador de paquetes**.
- Permite **solucionar problemas**, rastrear tráfico o detectar incidentes de seguridad.
- Muestra el tráfico **entrante y saliente por interfaz de red**.
- Utiliza **colores** para identificar distintos tipos de tráfico.

#### Usos:

- Filtrar tráfico por protocolos: HTTP, DNS, FTP, etc.
- Revisar **jerarquía de protocolos** y **conversaciones activas**.
- Examinar **desplazamiento lateral** (comunicación entre anfitriones internos).
- Exportar capturas para análisis posterior.

Filtros útiles (ejemplos):

| Filtro                | Descripción                        |
| --------------------- | ---------------------------------- |
| `ip.src==192.168.1.1` | Solo muestra paquetes desde esa IP |
| `tcp.port==80`        | Solo muestra tráfico HTTP          |
| `dns`                 | Filtra tráfico DNS                 |
| `http.request`        | Filtra solicitudes HTTP            |

> ✔️ La barra de filtros te dirá si el filtro es válido (verde) o inválido (rojo).
 
###  **Firewall pfSense y seguridad perimetral**

- **pfSense**: firewall **de código abierto**, puede actuar como **router y filtrador de paquetes**.
- Filtra según reglas definidas, puede bloquear **puertos, IPs, protocolos**.
- Permite:
    - Filtrado de paquetes por **estado de conexión**.
    - Usar **proxies** para controlar el tráfico entre host y destino.
    - Realizar **inspección profunda de paquetes**.

#### Tipos de firewall:

- **Software**: como pfSense, corre sobre un sistema operativo.
- **Hardware**: dispositivo físico dedicado.
- **Next Generation Firewall (NGFW)**: combinación con IDS/IPS, proxy, VPN, etc.
    

#### Conceptos adicionales:

- **DMZ**: zona desmilitarizada, expuesta al exterior (webservers, etc.).
- **NAT**: traducción de direcciones para permitir acceso entre redes.
- **Sandbox**: entorno controlado para analizar archivos o tráfico sospechoso.
- **Denegación implícita**: todo lo que no esté permitido por una regla, se bloquea automáticamente.

### **Otras herramientas mencionadas**

- **MITRE ATT&CK**: base de datos de tácticas y técnicas usadas por atacantes.
- **C2 (Command & Control)**: servidores usados por atacantes para controlar sistemas comprometidos.
    - **Indicador**: tráfico continuo entre dos hosts inusuales, comandos en texto claro.

### Notas adicionales:

- Se creó una lista de IPs a **excluir en escaneos Nmap** con la opción:

```bash
--excludefile archivo.txt
```
    
- Se generaron mapas de red para 3 dominios distintos.
- Usuarios y contraseñas de práctica:
    - `admin` / `Pfs3ns3P@ssw0rd`
    - `root` / `S0uthPAssw0rd`
    - Usuario analista: `analyst`