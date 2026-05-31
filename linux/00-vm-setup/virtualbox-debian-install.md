# Instalación de VM Linux — VirtualBox + Debian 12

## Software de virtualización
Se elige VirtualBox versión última estable (7.x) por las siguientes razones:
- Gratuito
- Multiplataforma
- Modelo de red explícito y fácil de aprender
- Estándar para empresas
- Se transfiere a PROXMOX fácilmente lo aprendido

## Sistema operativo
Debian GNU/Linux 12 (bookworm)
- Imagen: netinst amd64
- Descarga lo mínimo y obliga a configurar red durante la instalación como forma de aprendizaje

## Verificación de la ISO
Hash SHA256 comprobado antes de instalar con el hash que hay en debian.org de esta imagen
- HASH: ADFCBB50782AF99D457467F9B38C9E0FB3B1B6E211E0202F099AA58874B3F923

## Recursos de la VM
2 vCPU, 2 GB de RAM (suficiente para debian consola), 25 GB de disco (holgado sin desperdicio), disco dinámicamente reservado.

## Red
Modo NAT para tener acceso a internet, aislar del resto de la LAN y recibe IP del rango 10.0.2.0/24.

## Decisiones tomadas
- Consola sin escritorio, para acostumbrarnos a manejar solo terminal.
- Nomenclatura hl-lab-deb12-01 como nombre de VM y hostname, por lo que ambos coinciden, indicado en naming-conventions.md.
- Root sin contraseña, por lo que el usuario administrador está en grupo sudo.

## Snapshots
01-base-clean-install: snapshot base limpia
- Debian 12 recién instalado.
- Consola sin escritorio.
- SSH activo.
- NAT.
- Sin configuración adicional