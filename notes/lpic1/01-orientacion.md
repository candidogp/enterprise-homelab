# Bloque 1 — Orientación en el sistema y la terminal

## 1.1 — Filesystem Hierarchy Standard (FHS)

### Concepto

El sistema no está dividido por unidades como en Windows, todo cuelga del mismo árbol "/", desde el cual se montan los discos, particiones, etc. A partir de ahí, hay distintos directorios para cada función.

### Tabla de directorios de primer nivel
| Directorio        | Para qué sirve                                                                          |
|-------------------|-----------------------------------------------------------------------------------------|
| /etc              | Ficheros de configuración del sistema                                                   |
| /var              | Datos variables, como colas de correo, caché... que crece con el uso                    |
| /home             | Directorios personales de los usuarios                                                  |
| /root             | Directorio personal de root                                                             |
| /usr              | Programas y datos de usuarios instalados: binarios (/usr/bin), librerías, documentación |
| /bin, /sbin, /lib | Enlaces simbólicos dentro de /usr, binarios esenciales                                  |
| /tmp              | Ficheros temporales                                                                     |
| /boot             | El kernel y ficheros de arranque                                                        |
| /dev              | Discos representados como ficheros, ej: /dev/sda                                        |
| /proc, /sys       | Pseudo-sistemas de ficheros sobre el kernel y hardware del sistema                      |
| /opt, /srv, /mnt  | Software opcional, datos de servicios, puntos de montaje. También /media                |

### Comandos practicados
| Comando                     | Para qué sirve                                                                          |
|-----------------------------|-----------------------------------------------------------------------------------------|
| ls /                        | Muestra el directorio / con  sus carpetas como /bin, /home, etc.                        |
| ls -la /etc | head -30      | Lista 30 archivos de la carpeta /etc                                                    |
| cat /etc/os-release         | Lee el archivo que muestra la información del sistema                                   |
| ls /var/log                 | Lista los logs del sistemas (carpeta de logs)                                           |
| df -h                       | Muestra el espacio en disco                                                             |
| lsblk                       | Muestra las particiones de /dev/sda                                                     |
| cat /proc/cpuinfo           | Muestra la CPU intel asignada, confirmando las 2 vCPU que asigné a la VM                |
| cat /proc/meminfo           | Muestra el uso de la memoria en el sistema                                              |
| cd /proc && ls              | Nos movemos a la carpeta /proc y muestra la información de la misma                     |

### Dudas abiertas

#### ¿Qué es /proc exactamente y por qué cat /proc/cpuinfo da datos en vivo?

/proc no es un sistema de ficheros real en disco, un pseudo-filesystem. Cuando realizamos el comando cat /proc/cpuinfo no estamos revisando un fichero, estamos realizando una consulta al kernel para que te diga qué CPU hay instalada ahora mismo, es por esto que da datos en vivo. Se presenta como fichero por la filosofía UNIX, más sencillo para poder verlo con cat, filtrar con grep, etc.
Para resumir, /proc es una interfaz de texto sobre el estado del kernel y procesos en tiempo real. /sys lo hace sobre dispositivos y hardware
#### ¿Qué diferencia hay entre /usr/bin y /bin?

En Debian moderno, /bin es un enlace simbólico a /usr/bin. Históricamente sí había diferencias:
- /bin: binarios esenciales que deben estar disponibles si /usr no está montado, como ls, mv, cat, etc.
- /usr/bin: resto de programas de usuario.
- /sbin y /usr/sbin: misma metodología pero para binarios de administración del sistema, como fdisk, ifconfig, etc.

#### ¿Por qué /root está fuera de /home?

Normalmente /home se monta en particiones separadas para evitar pérdida de datos de usuarios tras una reinstalación del sistema, gestionar cuotas, montar /home en un servidor de red, etc.
Si el usuario root estuviese en /home en otra partición y esta no montara, no podríamos arreglar el problema, ya que no puede leer su .bashrc ni su .ssh/authorized_keys
Es por esto que /root vive en la partición raíz para garantizar que siempre está disponible.

#### ¿Por qué no existe /var/auth.log?

En Debian 12 no se instala por defecto rsyslog, servicio clásico para revisar logs. Los logs los gestiona systemd-journald, que incluye su propio sistema de logs, guardando los mismos en formato binario y se consulta con journalctl

## Bloque 1.2 - Navegación, rutas y comandos esenciales

### Rutas absolutas

Empieza en /. Describe la ubicación desde la raíz estés donde estés.

### Rutas relativas

Parte de donde estás ahora, por ejemplo, log/auth.log solo funciona si estás en /var

.  -> directorio actual
.. -> directorio padre
~  -> /home/usuario
-  -> directorio anterior

### Comandos relacionados

pwd                      # dónde estoy
cd /var/log              # ir (ruta absoluta)
cd ..                    # subir un nivel
cd ~                     # a mi home
cd -                     # al directorio anterior
ls -la                   # listar con detalle y ocultos
ls -lh /var/log          # tamaños legibles
tree -L 2                # árbol visual
file /etc/hostname       # qué tipo de fichero es
stat /etc/hostname       # metadatos detallados
cp, mv, rm, mkdir, touch # crear/copiar/mover/borrar
find /etc -name "*.conf" # buscar ficheros
which ls                 # dónde está el binario de un comando
type cd                  # qué es un comando (binario, builtin, alias)
history                  # tu historial de comandos

### Práctica

- Se crea directorio practica/ en /home/usuario.
- Se crean archivos prueba1 y prueba2 con el comando nano.
- Se mueve prueba1 a la carpeta home del usuario con mv ./prueba1 ~
- Se confirma que se ha movido correctamente.
- Se ejecuta find ~/practica -name "prueba2" y devuelve la ruta absoluta del fichero.
- Ejecutamos ls antes de eliminar el directorio y comprobamos que eliminaremos solo el archivo prueba2.
- Realizamos rm -rf practica/ y se borra todo su contenido.