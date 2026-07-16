# ADR-0002: Selección del switch gestionable del laboratorio

## Estado

Aceptada — 2026-07-15

## Contexto

La fase 2 del roadmap requiere segmentar la red del laboratorio en VLANs
802.1Q (gestión, servicios, laboratorio de simulación, etc.) partiendo de un
único host con NIC física única (`pve-node01`, ver ADR-0001). Esto exige un
switch gestionable capaz de trunking 802.1Q hacia el host y de actuar como
punto de segmentación entre el router del ISP y el resto del laboratorio.

Restricciones del proyecto:

- Presupuesto contenido (ver ADR-0001).
- Entorno doméstico: prioridad a bajo consumo y, si es posible, refrigeración
  pasiva (sin ruido de ventiladores).
- Mentalidad enterprise: se prioriza un switch con gestión real (VLANs
  802.1Q, trunking) frente a switches "smart" orientados a consumo.

## Decisión

Se selecciona un **Mikrotik CSS610-8G-2S+IN**: switch gestionable de 8
puertos gigabit RJ45 + 2 puertos SFP+ 10G, gestión vía SwOS (interfaz web,
sin CLI SSH), refrigeración pasiva (fanless), adquirido en PcComponentes por
111,99 € con 2 años de garantía.

## Consecuencias

### Positivas

- Soporta VLANs 802.1Q y trunking, requisito no negociable para la fase 2.
- Consumo máximo de 11 W y refrigeración pasiva: encaja con el perfil de
  bajo consumo y bajo ruido del laboratorio doméstico.
- Puertos SFP+ 10G disponibles para una futura ampliación de ancho de banda
  entre nodos, aunque no se usarán en las fases 2-3.

### Negativas / deuda técnica conocida

- **Sin CLI SSH**: SwOS solo ofrece gestión por interfaz web, lo que limita
  la automatización y el aprendizaje de una CLI de red representativa de un
  entorno enterprise (Cisco/Aruba). Se compensará con un laboratorio virtual
  GNS3/EVE-NG en fase 4 para practicar CLI de networking.
- **2 puertos SFP+ 10G sin uso previsto en fase 2-3**: sobredimensionado
  para las necesidades actuales del laboratorio (un único host con NIC
  gigabit).
- **Marca Mikrotik con menor peso en el mercado laboral canario** frente a
  Aruba/Cisco: se compensa documentando el laboratorio de simulación
  (GNS3/EVE-NG) en el portfolio público para cubrir esa exposición.

## Notas

- Decisión tomada en el chat especializado de Hardware del proyecto.
- La ficha técnica del equipo se mantiene en `hardware/network/sw-01.md`.
- El diseño detallado de VLANs (direccionamiento, plan de puertos) se define
  en el chat de Networking.
