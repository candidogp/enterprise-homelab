# State of the Lab

> Documento vivo. Refleja el estado **real** del homelab en cada momento.  
> Actualizar tras cada cambio significativo.

**Última actualización:** YYYY-MM-DD  
**Fase actual:** 0 — Preparación y fundamentos

---

## Resumen ejecutivo

Laboratorio en **fase de preparación**. Sin hardware dedicado todavía. 
Documentación y planificación en curso.

---

## Hardware

Estado: host principal adquirido, pendiente de recepción.

### Host principal — pve-node01

- Equipo: Lenovo ThinkCentre M920q Tiny
- CPU: Intel Core i5-9500T (6C/6T, 35W)
- RAM: 16 GB DDR4 (ampliable a 64 GB)
- Disco: 256 GB SSD
- Red: 1× NIC Intel Gigabit
- Estado: comprado en Ecoportátil, pendiente de recepción
- Documentación: `hardware/hosts/pve-node01.md`
- Decisión: `docs/architecture/decisions/0001-seleccion-host-virtualizacion.md`

### Próximas acciones de hardware

- [ ] Recepción y verificación física del equipo
- [ ] Rellenar datos pendientes en pve-node01.md (S/N, MAC, BIOS)
- [ ] Fase 2: ampliar RAM a 32 GB
- [ ] Fase 2: añadir SSD SATA 2.5" para backups (posible adelanto por capacidad)

---

## Red

**Estado:** switch gestionable recibido (`sw-01`), pendiente de configurar
VLANs 802.1Q. Hasta su configuración, la red sigue siendo plana bajo el
router del ISP.

### Switch gestionable — sw-01

- Equipo: Mikrotik CSS610-8G-2S+IN
- Puertos: 8× gigabit + 2× SFP+ 10G
- Gestión: SwOS (web GUI)
- Consumo: 11 W máximo
- Número de serie: HM30BFKDS63
- MAC: D0:EA:11:22:B2:E3
- Estado: recibido — pendiente de configuración de VLANs
- Documentación: `hardware/network/sw-01.md`
- Decisión: `docs/architecture/decisions/0002-seleccion-switch-gestionable.md`

### Próximas acciones de red

- [x] Rellenar versión de firmware/SwOS en sw-01 (2.21)
- [ ] Configurar VLANs 802.1Q en sw-01

Plan de direccionamiento futuro: pendiente de definir en chat de Networking 
(fase 1-2).

---

## Virtualización

**Estado:** sin hipervisor. Se usará VirtualBox/VMware Workstation en el PC 
personal durante fase 0 para refresco de Linux.

---

## Servicios desplegados

Ninguno todavía.

---

## Backups

No aplica todavía.

---

## Monitorización

No aplica todavía.

---

## Riesgos y deuda técnica conocida

- Router del ISP sin control avanzado: limitará networking hasta que se 
  introduzca firewall propio (fase 2).
- Sin segunda ubicación física: backup 3-2-1 requerirá pensar estrategia 
  off-site (fase 3).

---

## Próximos hitos

- [ ] Definir y adquirir hardware del servidor principal.
- [ ] Instalar entorno de virtualización temporal en PC personal.
- [ ] Refrescar Linux en VM (Debian o Ubuntu Server).
- [ ] Primer commit del repositorio con estructura inicial.
