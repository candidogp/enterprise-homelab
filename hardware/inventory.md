# Inventario de hardware

Última actualización: 2026-07-15

Inventario de equipos físicos del homelab. Cada equipo con ficha detallada
tiene enlace a su documento en `hosts/`.

## Equipos

### pve-node01 — Lenovo ThinkCentre M920q Tiny

| Campo               | Valor                                    |
|---------------------|------------------------------------------|
| Rol                 | Host de virtualización (Proxmox VE)      |
| Estado              | Pendiente de recepción                   |
| Fecha de compra     | 2026-05-XX                               |
| Proveedor           | Ecoportátil (ecoportatil.es)             |
| Precio              | 272,69 €                                 |
| Garantía            | 2 años (hasta 2028-05-XX)                |
| CPU                 | Intel Core i5-9500T (6C/6T, 35W TDP)     |
| RAM                 | 16 GB DDR4 (ampliable a 64 GB)           |
| Almacenamiento      | 256 GB SSD                               |
| Red                 | 1× NIC Intel Gigabit (integrada)         |
| Ficha detallada     | [hosts/pve-node01.md](hosts/pve-node01.md) |

### sw-01 — Mikrotik CSS610-8G-2S+IN

| Campo               | Valor                                    |
|---------------------|------------------------------------------|
| Rol                 | Switch gestionable (VLANs fase 2)        |
| Estado              | Recibido — pendiente de configuración    |
| Fecha de compra     | 2026-07-XX                                |
| Proveedor           | PcComponentes                             |
| Precio              | 111,99 € (IGIC aplicado en checkout)      |
| Garantía            | 2 años                                    |
| Puertos             | 8× gigabit + 2× SFP+ 10G                  |
| Gestión             | SwOS (web GUI)                            |
| Consumo             | 11 W máximo                               |
| Ficha detallada     | [network/sw-01.md](network/sw-01.md)      |

## Material pendiente de adquirir

| Material              | Fase prevista | Estado     |
|-----------------------|---------------|------------|
| RAM adicional (→32GB) | Fase 2 (mes 3)| Planificado|
| SSD SATA 2.5" (backups)| Fase 2 (mes 3)| Planificado|
| SAI / UPS             | Fase 3 (mes 5-6)| Planificado|
