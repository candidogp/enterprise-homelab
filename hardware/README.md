# Hardware

Documentación de todo el hardware físico del homelab: inventario,
fichas detalladas por equipo y registro de consumo eléctrico.

## Contenido

- [`inventory.md`](inventory.md) — Inventario resumido de todos los equipos.
- [`power-consumption.md`](power-consumption.md) — Registro de mediciones de consumo.
- [`hosts/`](hosts/) — Ficha técnica detallada de cada equipo.

## Convención de nomenclatura

| Rol                | Patrón        | Ejemplo      |
|--------------------|---------------|--------------|
| Nodo Proxmox       | `pve-nodeNN`  | `pve-node01` |
| Switch gestionable | `sw-NN`       | `sw-01`      |
| Firewall (futuro)  | `fw-NN`       | `fw-01`      |

## Estado actual

| Equipo       | Modelo                      | Rol                | Estado            |
|--------------|-----------------------------|--------------------|-------------------|
| `pve-node01` | Lenovo ThinkCentre M920q    | Host Proxmox       | Pendiente de recepción |
| `sw-01`      | Mikrotik CSS610-8G-2S+IN    | Switch gestionable | Recibido — pendiente de configuración |
