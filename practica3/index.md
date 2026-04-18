#  UD5 - P3 Active Directory

##  Introducción

En esta práctica se configura un dominio Windows con **Active Directory Domain Services (AD DS)**.

Un servidor actúa como controlador de dominio y un cliente Windows 11 se une a él, permitiendo la administración centralizada de usuarios, equipos y políticas dentro de la red.

---

##  1. Configuración del servidor

```bash
hostname
```

###  Explicación
Se cambia el nombre del servidor a `srv-ad01` para identificarlo dentro del dominio.

###  Objetivo
Preparar el servidor como controlador de dominio.

---

##  2. Instalación de AD DS

### 📖 Explicación
Se instala el rol **Active Directory Domain Services** desde Server Manager.

Este rol permite:
- Crear dominios Windows
- Gestionar usuarios y equipos
- Centralizar la administración de la red

---

##  3. Creación del dominio

### 📖 Explicación
Se promueve el servidor como **controlador de dominio** creando el bosque:

```
empresa.local
```

###  Objetivo
Convertir el servidor en el centro de gestión de la red.

---

##  4. Verificación del dominio

###  Explicación
Se comprueba que el dominio `empresa.local` se ha creado correctamente.

###  Objetivo
Confirmar que Active Directory está funcionando.

---

##  5. Creación de usuarios

###  Explicación
Se crean usuarios dentro del dominio:
- usuario1
- usuario2

###  Objetivo
Gestionar usuarios centralizados en el dominio.

---

##  6. Carpeta de perfiles

###  Explicación
Se crea y comparte la carpeta:

```
C:\perfiles
```

###  Objetivo
Guardar los perfiles de usuario en el servidor.

---

##  7. Perfiles móviles

```bash
\\srv-ad01\perfiles\%username%
```

###  Explicación
Permite que los usuarios mantengan su entorno en cualquier equipo del dominio.

###  Objetivo
Habilitar perfiles móviles centralizados.

---

##  8. Unión al dominio

###  Explicación
El equipo cliente `cli01` se une al dominio:

```
empresa.local
```

###  Objetivo
Permitir gestión centralizada del equipo.

---

## 9. Inicio de sesión

###  Explicación
Se inicia sesión con usuarios del dominio:

- empresa\usuario1  
- empresa\usuario2  

###  Objetivo
Comprobar autenticación en el dominio.

---

##  10. GPO (Group Policy)

###  Explicación
Se configuran políticas de grupo desde **Group Policy Management**.

###  Objetivo
Controlar reglas de seguridad de forma centralizada.

---

##  11. Aplicación de políticas

```bash
gpupdate /force
```

###  Explicación
Actualiza las políticas en el cliente.

###  Objetivo
Aplicar cambios de GPO inmediatamente.

---

##  12. Comprobación final

###  Resultado

Se verifica que:

- ✔ El equipo está unido al dominio  
- ✔ Los usuarios inician sesión correctamente  
- ✔ Los perfiles se guardan en el servidor  
- ✔ Las políticas de seguridad se aplican  

---

##  Conclusión

En esta práctica se ha configurado un dominio con Active Directory, permitiendo:

- Administración centralizada de usuarios
- Control de equipos en red
- Aplicación de políticas de seguridad
- Uso de perfiles móviles

Esto demuestra el funcionamiento básico de un entorno empresarial Windows.