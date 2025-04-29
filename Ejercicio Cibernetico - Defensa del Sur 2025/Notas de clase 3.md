# **Clase de Hoy: Cyberseguridad - Guardia Costera y Taiwan Cyber Defense**

## **Agenda**

- Review de la clase anterior
- Taiwan Cyber Brief
- Break
- Registro en Cyber Range
- Almuerzo
- **Network Mapping (NMAP)**

## **Review**

Resumen de ayer:

- **Misión y capacidad** de la Guardia Costera.
- **Políticas de ciberseguridad** de la Guardia Costera.
- **Órdenes Ejecutivas** para asegurar el ciberespacio.
- **Protección del espacio marítimo.**
- **Provisión de inteligencia.**
- Guardia Costera compuesta por **equipos de 39 miembros**.
- Ejecución del **plan de recuperación ante catástrofes**.

Se tocó también el tema de **Inteligencia de Ciberamenazas**.

## **Taiwan Cyber Brief**

**Políticas de Ciberseguridad en Taiwán:**

- **Misión:** Comunicación proactiva y construcción de un entorno confiable de ciberseguridad.
- **Asociación público-privada:** Mejora la resiliencia de la defensa nacional.

**Estructura de Comando:**

- Organizado por **capas**.
- Coordinación entre **NSC** y **NICS**.

**Objetivos Clave:**

- Defensa de ciberseguridad para toda la sociedad.
- Mejorar protección de **infraestructura crítica (IC)**.
- Fomentar industrias nacionales de ciberseguridad.
- Utilizar **tecnologías emergentes** (como IA y criptografía post-cuántica).

**Acciones Estratégicas:**

- Expansión del **desarrollo de expertos** en ciberseguridad.
- Construcción de sistemas de defensa para IC (alertas tempranas, equipos especializados).
- Mejorar la seguridad de control industrial (aumentar expertos en **OT**).
- Ejercicios simulados de ataque y defensa.

**Tecnología Destacada:**

- **CyberComp:** Sistema de cifrado de extremo a extremo basado en hardware.
    
    - Usa un **chip de comunicaciones** (no microcontrolador).
    - Implementa **doble cifrado** (dos claves).
    - Protege llamadas, mensajes y metadatos.
    - Mejora las prácticas de **seguridad móvil** (ya que los ataques llegaron vía SMS y llamadas).
    - La aplicación es sencilla, tipo app de mensajería.
        

**Notas sobre seguridad:**

- Confirmar la **identidad digital** de los usuarios.
- La importancia del cifrado avanzado ante ataques de actores estatales (como grupos chinos).

## **Ejercicio**

**Credenciales:**

- Password: `S0uthPAssw0rd`
- Users: `analyst`, `root`

## **Network Mapping (NMAP)**

### ¿Qué es la Enumeración?

- Crear una **línea base** de la red.
- Obtener **puertos, protocolos, versiones** y **flujo de tráfico**.
- Importante para detectar **cambios** y **vulnerabilidades**.

### **Antes de Escanear:**

- Tener **permiso** para escanear.
- Planificar (identificar sistemas sensibles que no se deben tocar).
- Verificar **comandos** antes de ejecutarlos.

### **Herramientas:**

- **Nmap:** Mapeo de redes (manual, por comandos).
- **Zenmap:** Versión gráfica de Nmap.

### **Escaneos Básicos de Nmap:**

- **TCP (`-sT`)**: Completa el "apretón de manos", muy detectable.
- **SYN (`-sS`)**: Más silencioso, no completa conexión (apretón de manos a medias).
- **FIN (`-sF`)**, **NULL (`-sN`)**, **XMAS (`-sX`)**: Escaneos para evadir firewalls, menos comunes hoy.
- **UDP (`-sU`)**: Escaneo de protocolos UDP (más lento).
- **Ping Scan (`-sP`)**: Detectar hosts activos.
- **Idle Scan (`-sI`)**: Usar dispositivos intermedios para escanear sin exponerse.
- **Escaneo de versiones (`-sV`)**: Detectar versión de servicios.
- **Detección de OS (`-O`)**: Detectar el sistema operativo.
- **Escaneo sin Ping (`-Pn`)**: Para redes que bloquean pings.

Ejemplo de comando usado hoy:
```bash
sudo nmap -sS -T4 192.168.15.0/24 --exclude 192.168.15.252
```
- `-sS`: Escaneo SYN (silencioso)
- `-T4`: Velocidad media-alta
- `--exclude`: Para omitir una IP.

### **Preguntas a resolver:**

1. ¿Qué comando muestra todas las opciones de Nmap?
    
    - `man nmap`
        
2. ¿Cuántos hosts hay en la red?
    
3. ¿Cuáles son sus direcciones IP?
    
4. ¿Qué puertos están abiertos en cada máquina?
    
5. ¿Cuántas máquinas Windows?
    
6. ¿Cuántas máquinas Linux?
    
7. ¿Qué servicios y versiones corren en cada host?
    
8. ¿Diferencia entre escaneo de intensidad 0 y 5?
    
9. ¿Qué host parece tener un arrendamiento seguro?
    
10. ¿Qué vulnerabilidades se detectaron?
    
11. ¿Qué host parece ser el más seguro?
    
12. ¿Crear un mapa de la red basado en los resultados?

