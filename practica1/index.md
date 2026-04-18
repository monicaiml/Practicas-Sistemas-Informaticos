# UD5 - P1 Redes Linux

## Introducción

En esta práctica se trabaja con dos máquinas virtuales Linux (cliente y servidor) dentro de una red local `192.168.50.0/24`.

El objetivo principal es aprender a:
- Configurar y analizar interfaces de red
- Verificar conectividad entre equipos
- Gestionar servicios de red en Linux
- Utilizar herramientas básicas de administración del sistema

---

## 1. Interfaces de red

```bash
ip a
```

###  Explicación
Este comando muestra todas las interfaces de red del sistema, tanto físicas como virtuales.

###  Información que obtenemos:
- Nombre de la interfaz (ej: `enp0s3`, `ens33`)
- Dirección IP asignada
- Dirección MAC (identificador físico de la tarjeta de red)
- Estado de la interfaz (UP/DOWN)

###  Objetivo
Verificar qué interfaces están activas y qué IP tiene asignada cada máquina.

---

##  2. Configuración de red

```bash
ip addr
ip route
```

###  Explicación
- `ip addr`: muestra configuración IP detallada
- `ip route`: muestra las rutas de red del sistema

### Información:
- IP local del equipo
- Máscara de red
- Puerta de enlace (gateway)
- Tabla de rutas

###  Objetivo
Comprobar cómo se comunica el sistema dentro de la red local.

---

##  3. Hostname

```bash
hostname
sudo hostnamectl set-hostname srv01
sudo hostnamectl set-hostname cli01
```

###  Explicación
El hostname es el nombre del equipo dentro de la red.

###  Configuración:
- Servidor → `srv01`
- Cliente → `cli01`

###  Objetivo
Identificar claramente cada máquina en la red.

---

##  4. Netplan (configuración de red fija)

```bash
sudo nano /etc/netplan/01-netcfg.yaml
sudo netplan apply
```

###  Explicación
Netplan se utiliza en Ubuntu para configurar la red de forma permanente.

###  Objetivo
Asignar una IP fija para evitar cambios tras reinicios.

---

##  5. Ping (conectividad)

```bash
ping 192.168.50.10
```

###  Explicación
`ping` envía paquetes ICMP para comprobar conectividad entre equipos.

###  Objetivo
Verificar que ambas máquinas se pueden comunicar correctamente.

---

##  6. Archivo hosts

```bash
sudo nano /etc/hosts
ping srv01
```

###  Explicación
Permite asignar nombres a direcciones IP manualmente.

###  Objetivo
Evitar usar IPs y trabajar con nombres de equipos.

---

##  7. Rutas del sistema

```bash
ip route
```

###  Explicación
Muestra cómo se envía el tráfico de red dentro del sistema.

###  Objetivo
Comprobar la ruta por defecto y la red local.

---

##  8. Puertos abiertos

```bash
ss -tuln
```

###  Explicación
Muestra qué servicios están escuchando conexiones en el sistema.

###  Objetivo
Detectar servicios activos como SSH, HTTP, etc.

---

##  9. SSH (acceso remoto)

```bash
sudo apt install openssh-server
sudo systemctl status ssh
```

###  Explicación
SSH permite acceder de forma remota a otro equipo de forma segura.

###  Objetivo
Habilitar administración remota del servidor.

---

## 10. Acceso remoto

```bash
ssh usuario@192.168.50.10
whoami
hostname
```

###  Explicación
Permite conectarse a otro equipo dentro de la red.

###  Objetivo
Comprobar acceso remoto funcional entre cliente y servidor.

---

##  11. Estado de red

```bash
ip link
```

###  Explicación
Muestra el estado físico de las interfaces de red.

###  Estados posibles:
- UP → activa
- DOWN → inactiva

---

##  12. Tabla ARP

```bash
ip neigh
```

###  Explicación
Relaciona direcciones IP con direcciones MAC.

###  Objetivo
Ver qué dispositivos están conectados en la red local.

---

##  13. Transferencia de archivos (SCP)

```bash
scp archivo.txt usuario@192.168.50.10:/home/usuario
```

###  Explicación
Permite copiar archivos entre máquinas usando SSH.

###  Objetivo
Transferir archivos de forma segura en la red.

---

##  14. Control del servicio SSH

```bash
sudo systemctl stop ssh
sudo systemctl start ssh
```

###  Explicación
Permite detener y arrancar el servicio SSH.

###  Objetivo
Verificar que el servicio responde correctamente.

---

##  15. Verificación tras reinicio

```bash
ip a
hostname
systemctl status ssh
```

###  Explicación
Después de reiniciar, se comprueba que la configuración se mantiene.

###  Objetivo
Confirmar persistencia de la configuración del sistema.

---

##  Conclusión

En esta práctica se han aprendido conceptos fundamentales de redes en Linux:

- Configuración de interfaces
- Gestión de IPs y rutas
- Conectividad entre equipos
- Administración de servicios como SSH
- Transferencia de archivos segura

Esto permite entender el funcionamiento básico de redes en sistemas Linux y su administración.